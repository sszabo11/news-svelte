<script lang="ts">
	import Sidebar from '$lib/Sidebar.svelte';
	import { onMount } from 'svelte';
	import { AirNotice } from 'airnotice-events';
	import { dev } from '$app/environment';
	import { initAirNotice } from 'airnotice-svelte';
	import { env } from '$env/dynamic/public';

	let { children } = $props();

	onMount(() => {
		AirNotice.init('brand_grnojegojre', true);
	});
	initAirNotice({
		apiKey: env?.PUBLIC_AIRNOTICE_DEV_KEY,
		showUnitStatus: true,
		autoSave: true
	});
</script>

<svelte:head>
	<script
		data-api-key="2cd3fcd2-8f59-46f9-baf4-3259272ea764"
		src="https://media.airnotice.co/place/index.js"
		id="ads-cdn"
	></script>

	{#if !dev}
		<script
			id="airnotice-events"
			data-key="13965b5a-38e8-4dd6-b349-0cf88ea4e693"
			src={`https://media.airnotice.co/events/index.js?meow=${performance.now()}`}
		></script>
	{/if}
</svelte:head>
<div class="app">
	<Sidebar />
	<div class="page">
		{@render children()}
	</div>
</div>

<style>
	:global(body) {
		width: 100vw;
		margin: 0;
		padding: 0;
		background-color: black;
		color: white;
		font-family: 'Instrument Serif';
	}

	.app {
		display: flex;
	}

	.page {
		padding: 30px 40px;
		box-sizing: border-box;
	}

	.page {
		width: calc(100vw - 60px);
	}
</style>
