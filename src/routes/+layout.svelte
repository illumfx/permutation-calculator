<script lang="ts">
	import Footer from "./Footer.svelte";

	let { children } = $props();
	let currentYear = $state(0);

	currentYear = new Date().getFullYear();
</script>

<nav>
	<a href="/">Home</a>
	<a href="/about">About</a>
</nav>

{@render children()}

<Footer {currentYear} />

<style>
	nav {
		text-align: right;
	}

	nav a {
		padding: 2px;
		margin: 4px;
	}
</style>
