<script context="module">
	export const load = async ({ fetch }) => {
		const res = await fetch('/api/posts.json');
		const posts = await res.json();
		return {
			props: {
				posts
			}
		};
	};
</script>

<script>
	export let posts;
</script>

<h1>Rakesh's Blog</h1>
{#each posts as post}
	<h2>{@html post.title.rendered}</h2>
	<p>{@html post.excerpt.rendered}</p>
	<a href={`/posts/${post.id}`}>Read More...</a>
{/each}
