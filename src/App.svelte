<script>
	import { onMount } from 'svelte';
	import List from './List.svelte';
	import Item from './Item.svelte';
	import Navbar from './Navbar/Navbar.svelte';

	let item;
	let page;

	const isDark = window.matchMedia("(prefers-color-scheme:dark)").matches

	async function hashchange() {
		// the poor man's router!
		const path = window.location.hash.slice(1);
		if (path.startsWith('/item')) {
			const id = path.slice(6);
			item = await fetch(`https://node-hnapi.herokuapp.com/item/${id}`).then(r => r.json()); // fetch article from api
			window.scrollTo(0,0);
		} else if (path.startsWith('/top')) {
			page = +path.slice(5); // get page num
			item = null;
		} else {
			window.location.hash = '/top/1';
		}
	}

	onMount(hashchange);
</script>

<svelte:window on:hashchange={hashchange}/>

<Navbar {isDark}/>

<svelte:head>
	<link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css" rel="stylesheet"/>
</svelte:head>

<main>
	{#if item}
		<Item {item} returnTo="#/top/{page}"/>
	{:else if page}
		<List {page}/>
	{/if}
</main>

<style>
	:root{
		--bg-color: #f2eee2;
		--text-color: #000;
		--bg-dark: #1d3040;
		--text-dark: #fff;

		--a: #462fdd;
		--a-visited: #483d8b;
		--a-dark: #fcbe5b;
		--a-dark-visited: #be934c;

		--max-w: 800px;
	}

	:global(body) {
		background-color: var(--bg-color);
		color: var(--text-color);
		transition: background-color 0.3s
	}

	:global(body.dark-mode) {
		--bg-color: var(--bg-dark);
		--text-color: var(--text-dark);
	}

	main {
		position: relative;
		max-width: var(--max-w);
		margin: 0 auto;
		min-height: 101vh;
		padding: 1em;
	}

	main :global(.meta) {
		color: #999;
		font-size: 12px;
		margin: 0 0 1em 0;
	}

	:global(a:link) {
		color: var(--a);
		text-decoration: none;
	}

	:global(a:hover) {
		text-decoration: underline;
	}

	:global(a:visited) {
		color: var(--a-visited);
	}

	:global(.dark-mode a:link) {
		color: var(--a-dark);
	}

	:global(.dark-mode a:visited) {
		color: var(--a-dark-visited);
	}
</style>