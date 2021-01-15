<script>
async function getData() {
        const res = await fetch('https://data.gov.lv/dati/lv/api/3/action/datastore_search?resource_id=610910e9-e086-4c5b-a7ea-0a896a697672&limit=100');
        const data = await res.json()
        const result = data.result.records
        return result
	}
	async function getData2() {
        const res = await fetch('https://cp55675.chost.lv/wp-json/wp/v2/posts');
        const data = await res.json()
        const result = data
        return result
    }
</script>





{#await getData2()}
	loading....
{:then posts}
	{#each posts as post}
		<section>
			{post.title.rendered}
			{post.content.rendered}
		</section>
	{/each}

{:catch e}
	error {e}
{/await}



{#await getData()}
	loading....
{:then posts}
	{#each posts as post}
		<section>
			{post._id}
			{post.Numurs}
			{post.Nosaukums}
			{post.Aktīvs}
			{post.Reģistrēts}
			{post.Izslēgts}
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