<script>
	const wordpress_url = "nallus.com"

	async function getData() {
		const response = await fetch("https://" + wordpress_url + "/wp-json/wp/v2/posts");

		if (response.ok) {
			return response.json();

		} else {
			throw new Error('there was a problem with fetch');
		}
	}
</script>

{#await getData()}
	loading....
{:then posts}
	{#each posts as post}
		<section>
			<h2>{post.title.rendered}</h2>
			<p>{@html post.content.rendered}</p>
		</section>
	{/each}

{:catch e}
	error {e}
{/await}

<style>
	section{
		margin: 0 auto;
		max-width:720px;
	}
</style>