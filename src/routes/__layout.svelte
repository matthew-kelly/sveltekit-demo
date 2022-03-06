<script>
	import Header from '$lib/Header.svelte';
	import '../app.css';
</script>

<div class="w-full min-h-screen flex flex-col align-middle">
	<Header />
	<main class="mx-5 grow">
		<slot />
	</main>
	<footer class="flex-none text-center">&copy; 2022</footer>
</div>
