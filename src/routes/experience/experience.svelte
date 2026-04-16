<script lang="ts">
	import { data } from '$lib/db/data';

	const jobs = data.work.filter((w) => w?.company || w?.title);
</script>

<div id="experience" class="experience-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Experience</h3>

	<div class="timeline my-4">
		{#each jobs as work, i}
			<div class="fade-in-up timeline-entry" style="animation-delay: {i * 70}ms">
				<div class="timeline-left">
					<div class="timeline-dot"></div>
					{#if i < jobs.length - 1}
						<div class="timeline-line"></div>
					{/if}
				</div>

				<div class="timeline-card">
					<div class="timeline-card-header">
						<div>
							<h4 class="font-semibold leading-tight">{work?.company || work?.title}</h4>
							{#if work.role}
								<p class="mt-0.5 text-sm text-muted-foreground">{work.role}</p>
							{/if}
						</div>
						<div class="flex flex-col items-end gap-1">
							<span class="year-badge">{work.year}</span>
							{#if work.address}
								<span class="text-xs text-muted-foreground">{work.address}</span>
							{/if}
						</div>
					</div>

					{#if work.technologies}
						<div class="mt-3 flex flex-wrap gap-1.5">
							{#each work.technologies.split(', ') as tech}
								<span class="tech-chip">{tech}</span>
							{/each}
						</div>
					{/if}

					{#if work.description}
						<div class="exp-desc mt-3 text-sm leading-relaxed text-muted-foreground">
							{@html work.description}
						</div>
					{/if}
				</div>
			</div>
		{/each}
	</div>
</div>

<style>
	.timeline {
		display: flex;
		flex-direction: column;
		gap: 0;
	}

	.timeline-entry {
		display: flex;
		gap: 16px;
		align-items: flex-start;
	}

	.timeline-left {
		display: flex;
		flex-direction: column;
		align-items: center;
		flex-shrink: 0;
		padding-top: 18px;
	}

	.timeline-dot {
		width: 12px;
		height: 12px;
		border-radius: 9999px;
		flex-shrink: 0;
		background: linear-gradient(135deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240));
		box-shadow: 0 0 0 3px oklch(0.55 0.18 240 / 0.15);
		z-index: 1;
	}

	.timeline-line {
		width: 2px;
		flex: 1;
		min-height: 24px;
		background: linear-gradient(
			to bottom,
			oklch(0.55 0.18 240 / 0.3),
			oklch(0.55 0.18 240 / 0.05)
		);
		margin-top: 4px;
	}

	.timeline-card {
		flex: 1;
		border: 1px solid var(--border);
		border-radius: var(--radius-lg);
		padding: 16px;
		margin-bottom: 16px;
		background: var(--card);
		transition: box-shadow 200ms ease, transform 200ms ease, border-color 200ms ease;
	}

	.timeline-card:hover {
		box-shadow: 0 4px 24px oklch(0.55 0.18 240 / 0.12);
		transform: translateX(2px);
		border-color: oklch(0.55 0.18 240 / 0.3);
	}

	.timeline-card-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		flex-wrap: wrap;
		gap: 8px;
	}

	.year-badge {
		font-size: 0.7rem;
		font-weight: 600;
		padding: 2px 8px;
		border-radius: 9999px;
		border: 1px solid var(--border);
		background: var(--muted);
		color: var(--muted-foreground);
		white-space: nowrap;
	}

	.exp-desc :global(ul) {
		list-style: disc;
		padding-left: 1.25rem;
		margin-top: 0.5rem;
	}

	.exp-desc :global(li) {
		margin-bottom: 4px;
	}

	.exp-desc :global(a) {
		color: oklch(0.5 0.2 240);
		text-decoration: underline;
		text-underline-offset: 2px;
	}
</style>
