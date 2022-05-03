<script>
	import { onMount } from 'svelte';
	import List from './List.svelte';
	import Item from './Item.svelte';
	
	let item;
	let page;

	async function hashchange() {
		// the poor man's router!
		const path = window.location.hash.slice(1);

		if (path.startsWith('/item')) {
			const id = path.slice(6);
			item = await fetch(`https://node-hnapi.herokuapp.com/item/${id}`).then(r => r.json()); // fetch article from api

			window.scrollTo(0, 0);
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

<main>

	{#if item}
		<Item {item} returnTo="#/top/{page}"/>
	{:else if page}
		<List {page}/>
	{/if}
	<center>Made with ❤️ by <a href="https://www.github.com/cveinnt">Vincent Wu</a></center>
</main>

<style>
	main {
		position: relative;
		max-width: 800px;
		margin: 0 auto;
		min-height: 101vh;
		padding: 1em;
	}

	main :global(.meta) {
		color: #999;
		font-size: 12px;
		margin: 0 0 1em 0;
	}

	main :global(a) {
		color: rgb(100, 78, 245);
		text-decoration: none;
	}

	main :global(a:hover) {
		text-decoration: underline;
	}

	main :global(a:visited) {
		color: rgb(72, 61, 139);
	}
</style>