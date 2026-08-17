<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { page } from '$app/state';

	let { children } = $props();
</script>

<svelte:head>
	<title>{page.data.title ?? 'Veniamin Medanov'}</title>
	<meta
		name="description"
		content={page.data.description ?? 'Veniamin is a 13 year old software engineer.'}
	/>
	<link rel="icon" href={favicon} />
</svelte:head>
{@render children()}
