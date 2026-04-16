<script lang="ts">
	import { afterNavigate } from '$app/navigation';
	import { page } from '$app/state';
	import Button from '$lib/components/ui/button/button.svelte';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import * as Sheet from '$lib/components/ui/sheet/index.js';
	import {
		Box,
		BriefcaseBusiness,
		FileUser,
		GraduationCap,
		Menu,
		Shapes,
		SunMoon,
		House
	} from '@lucide/svelte';

	import { mode, toggleMode as _toggleMode } from 'mode-watcher';

	import resume from '../../../public/images/Mittakola-Prashanth-Resume.pdf';

	const toggleMode = () => {
		_toggleMode();
		document.documentElement.classList.toggle('dark');
	};

	const isActive = (href: string) => {
		if (href === '/') return page.url.pathname === '/';
		return page.url.pathname.startsWith(href);
	};

	const navBarData = {
		items: [
			{
				title: 'Home',
				icon: House,
				href: '/'
			},
			{
				title: 'Skills',
				icon: Shapes,
				href: '/skills'
			},
			{
				title: 'Experience',
				icon: BriefcaseBusiness,
				href: '/experience'
			},
			{
				title: 'Projects',
				icon: Box,
				href: '/projects'
			},
			{
				title: 'Education',
				icon: GraduationCap,
				href: '/education'
			},
			{
				title: 'Resume',
				icon: FileUser,
				href: resume,
				download: 'Mittakola-Prashanth-Resume.pdf',
				target: '_blank'
			}
		]
	};

	let open = $state(false);
	afterNavigate((e) => {
		open = false;
	});
</script>

<nav>
	{#snippet navItems()}
		{#each navBarData.items as { download, target, ...item }}
			<a href={item.href} {download} {target} class="nav-link" class:active={isActive(item.href)}>
				<Button class="flex flex-row items-center justify-center gap-2" variant="ghost">
					<span class="text-base"><item.icon /></span>
					<span>{item.title}</span>
				</Button>
			</a>
		{/each}
	{/snippet}

	<div class="nav-bar absolute top-0 right-0 left-0 z-10 flex h-[52px] w-full flex-row items-center px-4 sm:px-8">
		<!-- larger than sm -->
		<div class="hidden w-full flex-row items-center sm:hidden md:flex">
			<a href={'/'} class="brand-link">
				<h2 class="brand flex items-center justify-center font-mono text-[clamp(0.9rem,1.8vw,1.3rem)] font-semibold">
					<span class="brand-icon mr-2">{`</>`}</span>
					<span>Prashanth Mittakola</span>
				</h2>
			</a>
			<div class="flex flex-[2] flex-row items-center justify-center gap-1">
				{@render navItems()}
			</div>
			<Button onclick={toggleMode} variant="ghost" class="rounded-full">
				<span class="text-base">
					<SunMoon />
				</span>
			</Button>
		</div>

		<!-- sm -->
		<div class="flex w-full flex-row items-center sm:flex md:hidden">
			<a href={'/'} class="brand-link flex flex-[2] flex-row items-center justify-center">
				<h2 class="brand flex items-center justify-center font-mono text-[clamp(0.9rem,2vw,1.3rem)] font-semibold">
					<span class="brand-icon mr-2">{`</>`}</span>
					<span>Prashanth Mittakola</span>
				</h2>
			</a>
			<div class="flex flex-row items-center justify-end">
				<Sheet.Root bind:open onOpenChange={(val) => (open = val)}>
					<Sheet.Trigger>
						<Menu />
					</Sheet.Trigger>
					<Sheet.Content>
						<Sheet.Header class="p-2">
							<Sheet.Title class="hidden">Menu</Sheet.Title>
						</Sheet.Header>
						{@render navItems()}
						<Separator />
						<a href={'#'}>
							<Button
								onclick={toggleMode}
								class="flex flex-row items-center justify-center gap-2"
								variant="ghost"
							>
								<span class="text-base"><SunMoon /></span>
								<span>{mode.current}</span>
							</Button>
						</a>
					</Sheet.Content>
				</Sheet.Root>
			</div>
		</div>
	</div>
</nav>

<style>
	nav {
		display: flex;
		justify-content: center;
	}

	.nav-bar {
		border-bottom: 1px solid oklch(0 0 0 / 0.08);
		background: oklch(0.98 0.005 240 / 0.7);
		backdrop-filter: blur(20px);
		-webkit-backdrop-filter: blur(20px);
	}

	:global(.dark) .nav-bar {
		border-bottom-color: oklch(1 0 0 / 0.08);
		background: oklch(0.129 0.042 265 / 0.75);
	}

	.brand-link {
		text-decoration: none;
	}

	.brand {
		color: inherit;
	}

	.brand-icon {
		background: linear-gradient(135deg, oklch(0.65 0.22 200), oklch(0.55 0.2 240));
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		color: transparent;
		font-weight: 700;
	}

	.nav-link {
		text-decoration: none;
		position: relative;
	}

	.nav-link.active :global(button) {
		background-color: oklch(0.55 0.18 240 / 0.12);
		color: oklch(0.5 0.2 240);
	}

	:global(.dark) .nav-link.active :global(button) {
		background-color: oklch(0.65 0.18 240 / 0.15);
		color: oklch(0.75 0.18 240);
	}
</style>
