<script lang="ts">
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import * as Card from '$lib/components/ui/card/index.js';
	import Education from './education/education.svelte';
	import Experience from './experience/experience.svelte';
	import Skills from './skills/skills.svelte';
	import Projects from './projects/projects.svelte';

	import prashanthImage from '../public/images/prashanth.jpg';
	import certificatePythonImage from '../public/images/achievements/certificate-python.png';
	import certificateGoogleAdsFundamentalsImage from '/src/public/images/achievements/certificate-google-ads-fundamentals.png';
</script>

<svelte:head>
	<title>Prashanth Mittakola</title>
	<meta name="description" content="Prashanth mittakola app" />

	<link
		rel="stylesheet"
		type="text/css"
		href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css"
	/>
</svelte:head>

<!-- Info -->
<div id="info-section" class="info-wrapper my-6 flex flex-col justify-around gap-6 sm:flex-row sm:gap-4">
	<div class="info-wrapper-text flex flex-col justify-center gap-3">
		<div class="flex items-center gap-2">
			<span class="rounded-full border border-cyan-500/30 bg-cyan-500/10 px-3 py-1 text-xs font-semibold tracking-widest text-cyan-600 uppercase dark:border-cyan-400/30 dark:bg-cyan-400/10 dark:text-cyan-400">
				Frontend Developer
			</span>
		</div>
		<h1 class="hero-title font-mono text-[clamp(2rem,4vw,3rem)] font-bold leading-tight">
			Prashanth Mittakola
		</h1>
		<p class="max-w-lg text-base leading-relaxed text-muted-foreground">
			Passionate about building beautiful, accessible web experiences and performance optimization.
			I transform ideas into elegant, functional web solutions.
		</p>
	</div>
	<div class="info-wrapper-image flex justify-center">
		<div class="profile-image-wrapper">
			<img
				src={prashanthImage}
				alt="Prashanth Mittakola"
				class="max-w-56 rounded-full transition-transform duration-300 hover:scale-105 sm:max-w-64"
			/>
		</div>
	</div>
</div>

<Separator class="my-4" />
<Skills enableCarousel={true} />

<Separator class="my-4" />
<Experience />

<Separator class="my-4" />
<Education />

<!-- I ♥️ -->
<Separator class="my-6" />
<div id="i-love" class="i-love-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">I ♥️</h3>
	<Card.Root class="my-4 w-full backdrop-blur-sm">
		<Card.Description class="px-6 py-4 text-base"
			>Playing Chess, Music, Swimming, Learning new things...</Card.Description
		>
	</Card.Root>
</div>

<Separator class="my-6" />
<Projects />

<!-- contact -->
<Separator class="my-6" />
<div id="contact" class="contact-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Contact</h3>
	<Card.Root class="my-4 w-full backdrop-blur-sm">
		<Card.Header>
			<div class="flex flex-wrap gap-2">
				<Card.Title class="min-w-16">Email :</Card.Title>
				<Card.Description
					><a href="mailto:mittakolaprashanth@gmail.com" class="hover:underline hover:text-cyan-600"
						>mittakolaprashanth@gmail.com</a
					></Card.Description
				>
			</div>
			<div class="flex flex-wrap gap-2">
				<Card.Title class="min-w-16">Mob &nbsp;&nbsp;:</Card.Title>
				<Card.Description
					><a href="tel:+918866238837" class="hover:underline hover:text-cyan-600">+918866238837</a></Card.Description
				>
			</div>
		</Card.Header>
	</Card.Root>
</div>

<!-- achievements -->
<Separator class="my-6" />
<div id="achievements" class="achievements-section">
	<h3 class="section-heading my-4 text-center text-2xl font-bold">Achievements</h3>

	<Card.Root class="my-4 w-full px-8">
		<Card.Content class="flex flex-wrap justify-center gap-8 ">
			<div class="achivement-wrapper flex max-w-80 flex-col flex-wrap justify-around gap-4">
				<a target="_blank" href={certificatePythonImage}>
					<img
						src={certificatePythonImage}
						alt="certificate-python-prashanth-mittakola.png"
						class="border-2 border-gray-400 p-2"
					/>
				</a>
				<Card.Description class="text-center">
					Python Programming Certificate - Completed with
					<br />
					<a href="https://codewithmosh.com/" target="_blank" title="code with mosh">
						<em>Mosh Hamedani (Code with Mosh)</em>, 2020
					</a>
				</Card.Description>
			</div>
			<Separator class="my-1" />
			<div class="achivement-wrapper flex max-w-3xs flex-col flex-wrap justify-around gap-4">
				<a target="_blank" href={certificateGoogleAdsFundamentalsImage}>
					<img
						src={certificateGoogleAdsFundamentalsImage}
						alt="certificate-google-ads-fundamentals.png"
						class="border-2 border-gray-400 p-2"
					/>
				</a>
				<Card.Description class="text-center">
					Google Ads fundamentals
					<br />
					<em>year 2018</em>
				</Card.Description>
			</div>
		</Card.Content>
	</Card.Root>
</div>

<style>
	.hero-title {
		background: linear-gradient(135deg, oklch(0.55 0.22 200), oklch(0.5 0.2 240), oklch(0.55 0.22 280));
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		color: transparent;
	}

	.profile-image-wrapper {
		position: relative;
		display: inline-flex;
	}

	.profile-image-wrapper::before {
		content: '';
		position: absolute;
		inset: -4px;
		border-radius: 9999px;
		background: linear-gradient(135deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240), oklch(0.6 0.22 280));
		z-index: -1;
	}

	.profile-image-wrapper img {
		border: 4px solid transparent;
		background-clip: padding-box;
	}

	.section-heading {
		position: relative;
		display: inline-block;
		width: 100%;
	}

	.section-heading::after {
		content: '';
		display: block;
		width: 48px;
		height: 3px;
		margin: 6px auto 0;
		border-radius: 9999px;
		background: linear-gradient(90deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240));
	}
</style>
