<script context="module">
	export async function load() {
		const posts = import.meta.globEager('../../posts/*.md'); // stupid vscode thinks /* is starting a comment */
		const postsList = Object.values(posts);
		const postsMeta = postsList.map((post) => post.metadata);
		return {
			props: {
				posts: postsMeta
			}
		};
	}
</script>

<script>
	export let posts;
</script>

<main class="flex justify-between">
	<div class="grow">
		<h1 class="mb-1">Posts</h1>
		<slot />
	</div>
	<aside class="shrink-0 ml-1">
		<h5 class="font-bold">Archive</h5>
		<ul>
			{#each posts as post}
				<li><a sveltekit:prefetch href="/posts/{post.slug}">{post.title}</a></li>
			{/each}
			<li><a href="/posts/about">About</a></li>
		</ul>
	</aside>
</main>
