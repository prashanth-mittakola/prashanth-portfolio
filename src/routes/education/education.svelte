<script lang="ts">
	import * as Card from '$lib/components/ui/card/index.js';

	const entries = [
		{
			level: 'College',
			institution: 'S.R.K Institute of Computer Science',
			detail: 'B.Sc Computer Science',
			location: 'Surat, Gujarat, India'
		},
		{
			level: 'Secondary',
			institution: 'Samrat Vidyala',
			detail: null,
			location: 'Surat, Gujarat, India'
		},
		{
			level: 'Primary',
			institution: 'S.V.V High School',
			detail: null,
			location: 'Kesamudram, Warangal, Telangana, India'
		}
	];
</script>

<div id="education" class="education-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Education</h3>

	<div class="timeline my-4">
		{#each entries as entry, i}
			<div class="fade-in-up timeline-entry" style="animation-delay: {i * 80}ms">
				<div class="timeline-left">
					<div class="timeline-dot"></div>
					{#if i < entries.length - 1}
						<div class="timeline-line"></div>
					{/if}
				</div>

				<div class="timeline-card">
					<span class="level-badge">{entry.level}</span>
					<h4 class="mt-1.5 font-semibold leading-tight">{entry.institution}</h4>
					<p class="mt-0.5 text-sm text-muted-foreground">
						{#if entry.detail}{entry.detail} ·{/if}
						{entry.location}
					</p>
				</div>
			</div>
		{/each}
	</div>
</div>

<style>
	.timeline {
		display: flex;
		flex-direction: column;
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
		padding-top: 16px;
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
		padding: 14px 16px;
		margin-bottom: 16px;
		background: var(--card);
		transition: box-shadow 200ms ease, transform 200ms ease, border-color 200ms ease;
	}

	.timeline-card:hover {
		box-shadow: 0 4px 20px oklch(0.55 0.18 240 / 0.12);
		transform: translateX(2px);
		border-color: oklch(0.55 0.18 240 / 0.3);
	}

	.level-badge {
		font-size: 0.7rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.06em;
		padding: 2px 8px;
		border-radius: 9999px;
		background: oklch(0.55 0.18 240 / 0.1);
		color: oklch(0.45 0.2 240);
		border: 1px solid oklch(0.55 0.18 240 / 0.2);
	}

	:global(.dark) .level-badge {
		background: oklch(0.65 0.18 240 / 0.15);
		color: oklch(0.78 0.18 240);
		border-color: oklch(0.65 0.18 240 / 0.25);
	}
</style>
