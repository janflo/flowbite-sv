<script>
	import { Button } from 'flowbite-svelte';
	import { DarkMode } from 'flowbite-svelte';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
	import { Gallery } from 'flowbite-svelte';
	import { CarouselTransition } from 'flowbite-svelte';
	let showThumbs = false;
	let showCaptions = false;
	let showIndicators = false;
	//   let duration = 4000
	const images = [
		{
			id: 0,
			attribution: 'shoes',
			imgurl:
				'https://flowbite-svelte.com/images/carousel/cosmic-timetraveler-pYyOZ8q7AII-unsplash.webp'
		},
		{
			id: 1,
			attribution: 'small bag',
			imgurl:
				'https://flowbite-svelte.com/images/carousel/cristina-gottardi-CSpjU6hYo_0-unsplash.webp'
		},
		{
			id: 2,
			attribution: 'plants',
			imgurl:
				'https://flowbite-svelte.com/images/carousel/johannes-plenio-RwHv7LgeC7s-unsplash.webp'
		},
		{
			id: 3,
			attribution: 'watch',
			imgurl: 'https://flowbite-svelte.com/images/carousel/jonatan-pie-3l3RwQdHRHg-unsplash.webp'
		},
		{
			id: 4,
			attribution: 'watch',
			imgurl: 'https://flowbite-svelte.com/images/carousel/mark-harpur-K2s_YE031CA-unsplash.webp'
		}
	];
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
		<NavLi href="/">Home</NavLi>
		<NavLi href="/about" active={true}>About</NavLi>
		<NavLi href="/contact">Contact</NavLi>
	</NavUl>
</Navbar>
<div class="container mx-auto pt-10">
	<DarkMode {btnClass} />
	<div class="max-w-4xl mx-auto">
		<CarouselTransition
			{images}
			loop
			{showThumbs}
			{showCaptions}
			{showIndicators}
			transitionType="fade"
			duration={5000}
		/>
	</div>
</div>
