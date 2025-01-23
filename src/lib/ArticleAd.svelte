<script lang="ts">
	import { Ad } from 'svelte-adjust';

	type Props = {
		name: string;
	};

	let { name }: Props = $props();
</script>

<div class="article">
	<Ad {name} category="Travel" region="US" />
</div>

<style>
	.article {
		padding: 18px;
		width: 300px;
		height: 230px;
		background-color: #111111;
		display: flex;
		flex-direction: column;
	}
</style>
