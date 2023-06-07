<script>
	import { Hr, P } from 'flowbite-svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { DarkMode } from 'flowbite-svelte';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
	import {
		Footer,
		FooterBrand,
		FooterCopyright,
		FooterIcon,
		FooterLink,
		FooterLinkGroup
	} from 'flowbite-svelte';
	import { page } from '$app/stores';
	import { Sidebar, SidebarGroup, SidebarItem, SidebarWrapper } from 'flowbite-svelte';
	import Grid from 'svelte-grid-responsive';
	let spanClass = 'flex-1 ml-3 whitespace-nowrap';
	$: activeUrl = $page.url.pathname;
	let vCard = false;
	let btnClass =
		'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2';
</script>

<Navbar let:hidden let:toggle>
	<NavBrand href="/">
		<img
			src="https://flowbite.com/docs/images/logo.svg"
			class="mr-3 h-6 sm:h-9"
			alt="Flowbite Logo"
		/>
		<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
			Flowbite
		</span>
	</NavBrand>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden}>
		<NavLi href="/" active={true}>Home</NavLi>
		<NavLi href="/about">About</NavLi>
		<NavLi href="/contact">Contact</NavLi>
	</NavUl>
	<DarkMode {btnClass} />
</Navbar>
<div class="container mx-auto pt-10">
	<Grid container gutter={12}>
		<Grid xs={12} sm={6} md={4} lg={4}>
			<Sidebar class="dark:bg-slate-600 bg-slate-200 w-full">
				<SidebarWrapper class="dark:bg-slate-600 bg-slate-200">
					<SidebarGroup>
						<SidebarItem label="Home" href="/" active={activeUrl === '/'} />
						<SidebarItem label="About" href="/about" active={activeUrl === '/about'} />
						<SidebarItem label="Contact" href="/contact" active={activeUrl === '/contact'} />
					</SidebarGroup>
				</SidebarWrapper>
			</Sidebar>
		</Grid>
		<Grid xs={12} sm={6} md={8} lg={8}>
			<Card
				img="https://flowbite-svelte.com/images/image-1.webp"
				reverse={vCard}
				class="max-w-lg w-full p-4"
			>
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
					Noteworthy technology acquisitions 2021
				</h5>
				<p class="mb-3 font-normal text-gray-700 dark:text-gray-400 leading-tight">
					Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse
					chronological order.
				</p>
				<Button class=" mx-auto">
					Read more <svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="1.5"
						stroke="currentColor"
						class="w-5 h-5 ml-2"
						><path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"
						/></svg
					>
				</Button>
			</Card>
			<Toggle bind:checked={vCard} class="mt-4 italic dark:text-gray-500">Reverse</Toggle>
			<br />
		</Grid>
	</Grid>
</div>

<Hr class="my-4 mx-auto md:my-10" width="w-48" height="h-1" />
<Footer class="dark:bg-slate-600 bg-slate-200">
	<FooterCopyright href="/" by="J.Flo™" year={2023} />

	<FooterLinkGroup
		ulClass="flex flex-wrap items-center mt-1 text-sm text-gray-500 dark:text-gray-400 sm:mt-0"
	>
		<FooterLink href="/about">About</FooterLink>
		<FooterLink active={true} href="/">Home</FooterLink>
	
		<FooterLink href="/contact">Contact</FooterLink>
	</FooterLinkGroup>
</Footer>
