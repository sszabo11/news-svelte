<script lang="ts">
	import { Ad, Dynamic, Group } from 'svelte-adjust';
	import Article from '$lib/Article.svelte';
	import Header from '$lib/Header.svelte';
	import ArticleAd from '$lib/ArticleAd.svelte';
	import { onMount } from 'svelte';
	import { browser } from '$app/environment';
	import { articles } from '$lib/articles';

	let mounted = $state(false);
	onMount(() => {
		mounted = true;
		console.log('mounted');
	});
</script>

{#if mounted}
	<div class="page">
		<Header />
		<div class="header-ads">
			<div class="ad-meow">
				<Ad name="head-1" fill="height" category="Travel" region="US" />
			</div>
			<div class="ad-meow">
				<Ad name="meow" fill="height" category="Travel" region="US" />
			</div>
		</div>
		<section>
			<h4>For you</h4>
			<div class="articles">
				<Group name="for-you">
					{#each articles.sort(() => Math.random() - 0.5) as article, i}
						{#if i % 5 === 0}
							<ArticleAd priority={5} group="for-you" key={(i / 5 + 1).toString()} name="" />
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
							<ArticleAd group="trending" key={(i / 3 + 1).toString()} name="" />
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
							<ArticleAd group="breaking" key={(i / 4 + 1).toString()} name="" />
						{/if}
						<Article {...article} />
					{/each}
				</Group>
			</div>
		</section>
	</div>
{/if}

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
