<script lang="ts">
	import Sidebar from '$lib/Sidebar.svelte';
	import { initializeAds } from 'svelte-adjust';

	let { children } = $props();

	initializeAds(8);
</script>

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
