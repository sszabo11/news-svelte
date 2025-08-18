<script lang="ts">
	import Article from '$lib/Article.svelte';
	import Header from '$lib/Header.svelte';
	import ArticleAd from '$lib/ArticleAd.svelte';
	import { onMount } from 'svelte';
	import { browser } from '$app/environment';
	import { articles } from '$lib/articles';
	import { PUBLIC_ADJUST_KEY } from '$env/static/public';
	import { Ad, Group } from 'airnotice';

	let mounted = $state(false);
	onMount(() => {
		mounted = true;
	});
</script>

<!--
<svelte:head>
	<script
		data-api-key={PUBLIC_ADJUST_KEY}
		id="ads-cdn"
		src="http://127.0.0.1:53102/dist/index.min.js?site_id=8"
	></script>
</svelte:head>
-->

<div class="page">
	<Header />
	<div class="header-ads">
		<div class="ad-meow">
			<Ad name="head-1" />
		</div>
		<div class="ad-meow">
			<Ad name="cat" />
		</div>
	</div>
	<section>
		<h4>For you</h4>
		<div class="articles">
			<Group name="for-you">
				{#each articles.sort(() => Math.random() - 0.5) as article, i}
					{#if i % 5 === 0}
						<ArticleAd />
					{/if}
					<Article {...article} />
				{/each}
			</Group>
		</div>
	</section>
	<section>
		<h4>Trending</h4>
		<div class="articles">
			<Group name="trending">
				{#each articles.sort(() => Math.random() - 0.8) as article, i}
					{#if i > 3 && i % 3 === 0}
						<ArticleAd key={(i / 3 + 1).toString()} />
					{/if}
					<Article {...article} />
				{/each}
			</Group>
		</div>
	</section>
	<section>
		<h4>Breaking</h4>
		<div class="articles">
			<Group name="breaking">
				{#each articles.sort(() => Math.random() - 0.2) as article, i}
					{#if i > 2 && i % 4 === 0}
						<ArticleAd key={(i / 4 + 1).toString()} />
					{/if}
					<Article {...article} />
				{/each}
			</Group>
		</div>
	</section>
</div>

<style>
	.page {
		width: 100%;
		height: 100%;
		overflow-x: hidden;
	}

	.articles {
		display: flex;
		gap: 30px;
		overflow-x: auto;
	}

	.header-ads {
		display: flex;
		align-items: center;
	}

	.ad-meow {
		width: 300px;
		height: 200px;
	}

	section h4 {
		font-size: 24px;
		font-weight: 400;
	}
</style>
