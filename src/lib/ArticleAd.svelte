<script lang="ts">
	import { onMount } from 'svelte';
	import { Ad } from 'svelte-adjust';

	type Props = {
		name: string;
		key: string;
	};

	let { name, key }: Props = $props();

	onMount(() => {
		console.log('article mount');
	});
</script>

<div class="article">
	<div class="ad">
		<Ad name="fgrew" {key} category="Travel" region="US" borderRadius={0} />
	</div>
	<span>Promoted content</span>
</div>

<style>
	.article {
		padding: 18px;
		width: 200px;
		height: 230px;
		overflow: hidden;
		background-color: #111111;
		position: relative;
	}

	.ad {
		width: 100%;
		height: 200px;
	}

	span {
		position: absolute;
		font-size: 14px;
		color: #676767;
		bottom: 10px;
	}
</style>
