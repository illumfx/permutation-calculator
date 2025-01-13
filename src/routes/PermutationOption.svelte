<script lang="ts">
	let props = $props();
	let clicked = $state(false);

	function copyClipboard() {
		clicked = true;
		navigator.clipboard.writeText(props.permutation);
	}
</script>

<div class="permutationOption">
	<a class={clicked ? "copied" : "default"} href="." onclick={copyClipboard}>{props.permutation}</a>
</div>

<style>
	.permutationOption {
		margin-top: 10px;
	}

	a:hover {
		background-color: #fff3;
		border-radius: 5px;
		border-width: 10px;
	}

	a.copied {
		color: rgb(29, 243, 22);
	}
</style>
