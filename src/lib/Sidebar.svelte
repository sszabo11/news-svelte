<script lang="ts">
	import Account from './icons/Account.svelte';
	import Home from './icons/Home.svelte';
	import Logo from './icons/Logo.svelte';
	import Post from './icons/Post.svelte';
	import Trending from './icons/Trending.svelte';
</script>

<div class="sidebar">
	<div class="logo-container">
		<div class="logo">
			<Logo />
		</div>
	</div>
	<ul>
		<li class="item">
			<span class="tooltiptext">Home</span>
			<a href="/site/dashboard/"><Home /></a>
		</li>
		<li class="item">
			<span class="tooltiptext">Ads</span><a href="/"><Trending /></a>
		</li>
		<li class="item">
			<span class="tooltiptext">Analytics</span><a href="/site/dashboard/analytics"><Post /></a>
		</li>
		<li class="item">
			<span class="tooltiptext">Pro</span><a href="/purchase/banana/"><Account /></a>
		</li>
	</ul>
</div>

<style>
	.sidebar {
		width: 60px;
		border-right: 1px solid #f2f2f2;
		height: 100vh;
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		align-items: center;
		padding-top: 20px;
	}

	.logo-container {
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 60px;
	}

	.logo {
		display: flex;
		gap: 20px;
		align-items: center;
	}

	ul {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		gap: 35px;
		padding: 0;
		align-items: center;
	}

	li {
		list-style: none;
	}

	a {
		text-decoration: none;
		color: black;
	}

	.item {
		position: relative;
		display: inline-block;
	}

	.item .tooltiptext {
		visibility: hidden;
		width: 100px;
		background-color: #111111;
		color: white;
		text-align: center;
		padding: 6px 12px;
		border-radius: 6px;
		position: absolute;

		z-index: 1;
		bottom: 125%;
		left: 50%;
		margin-left: -50px;
		opacity: 0;
		transition: opacity 0.3s;
		display: none;
	}

	.item:hover .tooltiptext {
		visibility: visible;
		opacity: 1;
	}
</style>
