<script lang="ts">
	import { page } from '$app/state';
</script>

<div class="page">
	<h1>Buy product: {page.params.productId}</h1>
	<a href="./complete">Buy</a>
</div>

<style>
	h1 {
		font-size: 100px;
	}

	a {
		color: white;
	}
</style>
