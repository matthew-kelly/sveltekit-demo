<script context="module">
	export async function load({ url, params, props, fetch, session, stuff }) {
		try {
			const post = await import(`../../posts/${params.slug}.md`);

			return {
				props: {
					Post: post.default,
					title: post?.metadata?.title
				}
			};
		} catch (e) {
			// return {
			// 	redirect: '/posts',
			// 	status: 307
			// };
			return {
				error: 'Post not found',
				status: 404
			};
		}
	}
</script>

<script>
	export let Post;
	export let title;
</script>

<svelte:head>
	<title>SvelteKit Blog - {title}</title>
</svelte:head>

<article>
	<svelte:component this={Post} />
	<!-- <Post /> -->
</article>
