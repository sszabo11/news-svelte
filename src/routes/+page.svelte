<script lang="ts">
	import { Ad } from 'svelte-adjust';
	import Article from '$lib/Article.svelte';
	import Header from '$lib/Header.svelte';
	import ArticleAd from '$lib/ArticleAd.svelte';

	let articles: {
		src: string;
		title: string;
		date: Date;
		author: string;
	}[] = [
		{
			src: 'https://i.guim.co.uk/img/media/9e6108d84053066c2479a0bde0182a2361a9e407/1_0_2998_1800/master/2998.jpg?width=620&dpr=1&s=none&crop=none',
			title: 'The AI Revolution: How Machine Learning is Shaping the Future',
			date: new Date('2025-01-15'),
			author: 'Elena Harris'
		},
		{
			src: 'https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/09/a-laptop-on-a-table-with-some-ingredients-around-it-and-the-rust-logo-on-the-screen.jpg?q=49&fit=crop&w=1100&h=618&dpr=2',
			title: 'Why Rust is Taking Over the Programming World',
			date: new Date('2025-01-18'),
			author: 'Liam Carter'
		},
		{
			src: 'https://ibtlearning.africa/wp-content/uploads/2024/12/1708394467259-2.png',
			title: 'Top Cloud Computing Trends to Watch in 2025',
			date: new Date('2025-01-10'),
			author: 'Sophia Nguyen'
		},
		{
			src: 'https://cfotech.com.au/uploads/story/2024/11/13/techday_3cc8356b00639e1cc91f.webp',
			title: 'Blockchain Beyond Cryptocurrency: Real-World Use Cases',
			date: new Date('2025-01-12'),
			author: 'Ryan Patel'
		},
		{
			src: 'https://www.tetratech.com/wp-content/uploads/2023/09/Cybersecurity-Federal-IT-5.jpg',
			title: 'Cybersecurity in 2025: Tips to Stay Ahead of Threats',
			date: new Date('2025-01-19'),
			author: 'Avery Johnson'
		},
		{
			src: 'https://imageio.forbes.com/specials-images/imageserve/5db28252c538200007815c25/What-Is-5G-Technology-And-How-Must-Businesses-Prepare-For-It-/960x0.jpg?height=474&width=711&fit=bounds',
			title: 'How the 5G Rollout is Changing Global Connectivity',
			date: new Date('2025-01-07'),
			author: 'Noah Bennett'
		},
		{
			src: 'https://bernardmarr.com/wp-content/uploads/2023/11/The-10-Biggest-AR-VR-And-Immersive-Internet-Trends-In-2024.jpg',
			title: 'Exploring the Future of AR and VR Technologies',
			date: new Date('2025-01-22'),
			author: 'Mia Taylor'
		},
		{
			src: 'https://src.n-ix.com/uploads/2024/02/05/50dcd5d5-dd95-493a-8cce-35d16488fe09.webp',
			title: 'DevOps Best Practices for Scalable Software Development',
			date: new Date('2025-01-13'),
			author: 'Ethan Walker'
		},
		{
			src: 'https://assets.clevelandclinic.org/transform/2419787a-53b5-4f2a-aa36-47db8fa3ba79/ibm-quantum-system-one-ces-2020_50252942522_o_jpg?io=transform:fit,width:780',
			title: 'The Quantum Leap: What You Need to Know About Quantum Computing',
			date: new Date('2025-01-21'),
			author: 'Isabella Adams'
		},
		{
			src: 'https://media.licdn.com/dms/image/v2/D4E12AQHKGMqwbOGIqw/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1728021516479?e=2147483647&v=beta&t=fKZG1JLvlUaVQVmtJiVKkcU5FZ7UdkFs_BfKE9laKgQ',
			title: 'The Internet of Things: 2025 Trends and Predictions',
			date: new Date('2025-01-05'),
			author: 'Oliver Smith'
		}
	];
</script>

<div class="page">
	<Header />
	<div class="ad-container">
		<Ad name="page" fill="height" category="Travel" region="US" />
	</div>
	<section>
		<h4>For you</h4>
		<div class="articles">
			{#each articles.sort(() => Math.random() - 0.5) as article, i}
				{#if i % 5 === 0}
					<div class="feed-ad">
						<ArticleAd name={`feed-${i / 5}`} />
					</div>
				{/if}
				<Article {...article} />
			{/each}
		</div>
	</section>
	<section>
		<h4>Trending</h4>
		<div class="articles">
			{#each articles.sort(() => Math.random() - 0.8) as article}
				<Article {...article} />
			{/each}
		</div>
	</section>
	<section>
		<h4>Breaking</h4>
		<div class="articles">
			{#each articles.sort(() => Math.random() - 0.2) as article}
				<Article {...article} />
			{/each}
		</div>
	</section>
</div>

<style>
	.page {
		width: 100%;
	}

	.articles {
		display: flex;
		gap: 30px;
	}

	.ad-container {
		width: 100%;
		height: 200px;
	}

	section h4 {
		font-size: 24px;
		font-weight: 400;
	}
</style>
