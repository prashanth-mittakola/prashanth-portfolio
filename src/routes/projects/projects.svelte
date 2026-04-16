<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import BubbleSort from './bubble-sort/bubble-sort.svelte';
</script>

<div id="projects" class="projects-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Sample Projects</h3>
	<div class="flex flex-col gap-2">
		<BubbleSort />
	</div>
	<div class="my-6 flex items-center justify-center">
		<a href="/projects">
			<Button class="see-more-btn rounded-full px-6" variant="outline">
				See More Projects →
			</Button>
		</a>
	</div>
</div>

<style>
	.see-more-btn {
		border-color: oklch(0.55 0.18 240 / 0.4);
		color: oklch(0.5 0.2 240);
		transition: background 200ms ease, border-color 200ms ease, box-shadow 200ms ease;
	}

	.see-more-btn:hover {
		background: oklch(0.55 0.18 240 / 0.1);
		border-color: oklch(0.55 0.18 240 / 0.6);
		box-shadow: 0 0 16px oklch(0.55 0.18 240 / 0.2);
	}

	:global(.dark) .see-more-btn {
		border-color: oklch(0.65 0.18 240 / 0.4);
		color: oklch(0.75 0.18 240);
	}

	:global(.dark) .see-more-btn:hover {
		background: oklch(0.65 0.18 240 / 0.15);
		border-color: oklch(0.65 0.18 240 / 0.6);
		box-shadow: 0 0 16px oklch(0.65 0.18 240 / 0.25);
	}
</style>
