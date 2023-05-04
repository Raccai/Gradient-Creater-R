<script>
	import Card from "./Card.svelte";
	import MainBody from "./MainBody.svelte";
	import Header from "./Header.svelte";
</script>

<main>
	<Header />
	<Card>
		<MainBody />
	</Card>
</main>

<style>
	main {
		position: relative;
		display: flex;
		flex-direction: column;
	}
</style>