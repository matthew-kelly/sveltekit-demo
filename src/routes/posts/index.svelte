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

<svelte:head>
	<title>SvelteKit Blog</title>
</svelte:head>

<section class="text-gray-600 body-font overflow-hidden">
	<div class="container px-5 mx-auto">
		<div class="divide-y-2 divide-gray-100">
			{#each posts as post}
				<div class="py-8 flex flex-wrap md:flex-nowrap">
					<div class="md:w-64 md:mb-0 mb-6 flex-shrink-0 flex flex-col">
						<span class="font-semibold title-font text-gray-700">Post</span>
						<span class="mt-1 text-gray-500 text-sm">March 5, 2022</span>
					</div>
					<div class="md:flex-grow ml-2">
						<h2 class="text-2xl font-medium text-gray-900 title-font mb-2">
							{post.title}
						</h2>
						<a href="/posts/{post.slug}" class="text-indigo-500 inline-flex items-center mt-4"
							>Read
							<svg
								class="w-4 h-4 ml-2"
								viewBox="0 0 24 24"
								stroke="currentColor"
								stroke-width="2"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path d="M5 12h14" />
								<path d="M12 5l7 7-7 7" />
							</svg>
						</a>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
