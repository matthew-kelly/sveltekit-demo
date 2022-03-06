<script context="module">
	export function load({ error, status }) {
		return {
			props: {
				status,
				error
			}
		};
	}
</script>

<script>
	export let status;
	export let error;
</script>

<div class="flex flex-col items-center text-xl mt-5">
	<h1 class="text-2xl">Something went wrong!</h1>
	<h3>Error {status}: {error.message}</h3>
</div>
