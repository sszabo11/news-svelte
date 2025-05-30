<script lang="ts">
	import Sidebar from '$lib/Sidebar.svelte';
	import { onMount } from 'svelte';
	import { AirNotice } from 'airnotice-events';
	import { dev } from '$app/environment';

	let { children } = $props();

	onMount(() => {
		AirNotice.init('brand_grnojegojre', true);
	});

	let events = dev
		? 'http://127.0.0.1:8080/dist/index.min.js'
		: 'https://airnotice-events.s3.us-east-1.amazonaws.com/index.js';
</script>

<svelte:head>
	<script id="airnotice-events" data-api-key="meow" data-is-dev="true" src={events}></script>
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
