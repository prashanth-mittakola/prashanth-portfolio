<script lang="ts">
	import Header from './Header.svelte';
	import '../app.css';
	import { onNavigate } from '$app/navigation';

	let { children } = $props();

	onNavigate((navigation) => {
		if (!document.startViewTransition) return;
		return new Promise<void>((resolve) => {
			document.startViewTransition(async () => {
				resolve();
				await navigation.complete;
			});
		});
	});
</script>

<div class="app">
	<Header />

	<main style="view-transition-name: page-content">
		{@render children()}
	</main>

	<footer>
		<div class="footer-links">
			<a href="mailto:mittakolaprashanth@gmail.com">Email</a>
			<span aria-hidden="true">·</span>
			<a href="https://www.linkedin.com/in/prashanth-mittakola-13191b164/" target="_blank">LinkedIn</a>
			<span aria-hidden="true">·</span>
			<a href="https://github.com/prashanth-mittakola" target="_blank">GitHub</a>
			<span aria-hidden="true">·</span>
			<a href="tel:+918866238837">Phone</a>
		</div>
		<p class="footer-copy">© {new Date().getFullYear()} Prashanth Mittakola</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 6px;
		padding: 24px 16px;
		border-top: 1px solid oklch(0 0 0 / 0.08);
		margin-top: 2rem;
	}

	:global(.dark) footer {
		border-top-color: oklch(1 0 0 / 0.08);
	}

	.footer-links {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;
		gap: 8px;
		font-size: 0.8125rem;
	}

	.footer-links a {
		color: oklch(0.55 0.18 240);
		text-decoration: none;
		transition: color 150ms ease;
	}

	.footer-links a:hover {
		color: oklch(0.45 0.2 240);
		text-decoration: underline;
	}

	.footer-links span {
		color: oklch(0.7 0 0);
	}

	.footer-copy {
		font-size: 0.75rem;
		color: oklch(0.6 0.02 255);
	}
</style>
