<script>
	import * as Carousel from '$lib/components/ui/carousel/index.js';
	import { data } from '$lib/db/data';

	const { enableCarousel } = $props();
</script>

{#snippet skillItem(title)}
	{@const iconSrc = data.skillsWithDevIcons[title]}
	<div class="skill-item">
		<div class="skill-icon-wrap">
			{#if iconSrc}
				<img src={iconSrc} alt={title} class="skill-icon" />
			{:else}
				<span class="skill-icon-fallback">
					{title.slice(0, 2).toUpperCase()}
				</span>
			{/if}
		</div>
		<span class="skill-label">{title}</span>
	</div>
{/snippet}

<!-- svelte-ignore a11y_missing_attribute -->
<div id="skills" class="skills-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Skills</h3>

	{#if enableCarousel}
		<div class="my-4 flex justify-center">
			<Carousel.Root opts={{ align: 'center' }} class="w-[88%]">
				<Carousel.Content>
					{#each data.skills as title (title)}
						<Carousel.Item class="flex basis-1/2 items-center justify-center sm:basis-1/3 md:basis-1/4 lg:basis-1/5">
							{@render skillItem(title)}
						</Carousel.Item>
					{/each}
				</Carousel.Content>
				<Carousel.Previous />
				<Carousel.Next />
			</Carousel.Root>
		</div>
	{:else}
		<div class="skills-grid my-4">
			{#each data.skills as title, i (title)}
				<div class="fade-in-up" style="animation-delay: {i * 40}ms">
					{@render skillItem(title)}
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.skills-grid {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		gap: 10px;
	}

	.skill-item {
		width: 108px;
		height: 90px;
		border: 1px solid var(--border);
		border-radius: 12px;
		background: var(--card);
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 8px;
		padding: 10px 8px;
		box-sizing: border-box;
		transition: box-shadow 200ms ease, transform 200ms ease, border-color 200ms ease;
		cursor: default;
	}

	.skill-item:hover {
		box-shadow: 0 4px 18px oklch(0.55 0.18 240 / 0.15);
		transform: translateY(-3px) scale(1.03);
		border-color: oklch(0.55 0.18 240 / 0.35);
	}

	.skill-icon-wrap {
		width: 36px;
		height: 36px;
		flex-shrink: 0;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.skill-icon {
		width: 36px;
		height: 36px;
		object-fit: contain;
		display: block;
	}

	.skill-icon-fallback {
		width: 36px;
		height: 36px;
		border-radius: 8px;
		background: linear-gradient(135deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240));
		color: white;
		font-size: 11px;
		font-weight: 700;
		letter-spacing: 0.02em;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.skill-label {
		font-size: 0.68rem;
		font-weight: 500;
		text-align: center;
		line-height: 1.25;
		width: 100%;
		/* clamp to 2 lines */
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}
</style>
