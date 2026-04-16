<script>
	import * as Card from '$lib/components/ui/card/index';
</script>

<svelte:head>
	<title>Prashanth Mittakola - Projects</title>
</svelte:head>

<div class="projects-page">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Projects</h3>
	<div class="grid gap-4">
		<a href="/projects/bubble-sort" class="project-link fade-in-up" style="animation-delay: 0ms">
			<Card.Root class="project-card w-full">
				<Card.Content class="flex items-start gap-4 pt-5">
					<span class="project-num">01</span>
					<div>
						<Card.Title class="text-lg">Bubble Sort Visualizer</Card.Title>
						<p class="mt-1 text-sm text-muted-foreground">Simple sorting algorithm that repeatedly swaps adjacent elements, animated live.</p>
						<div class="mt-2 flex gap-2">
							<span class="tech-chip">JavaScript</span>
							<span class="tech-chip">SvelteKit</span>
						</div>
					</div>
				</Card.Content>
			</Card.Root>
		</a>

		<a href="https://react-file-explorer-mp.vercel.app/" class="project-link fade-in-up" style="animation-delay: 70ms" target="_blank" rel="noopener">
			<Card.Root class="project-card w-full">
				<Card.Content class="flex items-start gap-4 pt-5">
					<span class="project-num">02</span>
					<div>
						<Card.Title class="text-lg">File Explorer</Card.Title>
						<p class="mt-1 text-sm text-muted-foreground">A recursive file explorer built with React.js using custom hooks.</p>
						<div class="mt-2 flex gap-2">
							<span class="tech-chip">React.js</span>
							<span class="tech-chip">Custom Hooks</span>
						</div>
					</div>
				</Card.Content>
			</Card.Root>
		</a>

		<a href="https://next-js-13-movies-demo-app.vercel.app/" class="project-link fade-in-up" style="animation-delay: 140ms" target="_blank" rel="noopener">
			<Card.Root class="project-card w-full">
				<Card.Content class="flex items-start gap-4 pt-5">
					<span class="project-num">03</span>
					<div>
						<Card.Title class="text-lg">Next.js + Framer Motion Movies</Card.Title>
						<p class="mt-1 text-sm text-muted-foreground">Movie browsing app using Next.js v13, Framer Motion animations, and TheMovieDB API.</p>
						<div class="mt-2 flex flex-wrap gap-2">
							<span class="tech-chip">Next.js</span>
							<span class="tech-chip">Framer Motion</span>
							<span class="tech-chip">TheMovieDB</span>
						</div>
					</div>
				</Card.Content>
			</Card.Root>
		</a>
	</div>
</div>

<style>
	.project-link {
		text-decoration: none;
		color: inherit;
		display: block;
	}

	.project-card {
		transition: box-shadow 200ms ease, transform 200ms ease;
	}

	.project-card:hover {
		box-shadow: 0 4px 24px oklch(0.55 0.18 240 / 0.15);
		transform: translateY(-2px);
	}

	.project-num {
		font-size: 1.5rem;
		font-weight: 700;
		font-variant-numeric: tabular-nums;
		background: linear-gradient(135deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240));
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		color: transparent;
		flex-shrink: 0;
		line-height: 1;
		padding-top: 2px;
	}
</style>
