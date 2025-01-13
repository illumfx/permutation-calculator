<script lang="ts">
	import Header from "./Header.svelte";
	import NumberInput from "./NumberInput.svelte";
	import PermutationOption from "./PermutationOption.svelte";
	import Footer from "./Footer.svelte";

	let inputValue = $state("0");
	let currentYear = $state(0);
	let permutations: string[] = $state([]);

	currentYear = new Date().getFullYear();

	function calculatePermutations() {
		if (!inputValue) {
			permutations = [];
			return;
		}
		if (isFinite(Number(inputValue))) {
			permutations = getCombinations(inputValue.toString());
		}
	}

	function getCombinations(str: string): string[] {
		const permutationList: string[] = [];

		function permute(str: string, left: number, right: number): void {
			if (left === right) {
				if (!permutationList.includes(str)) {
					permutationList.push(str);
				}
			} else {
				for (let i = left; i <= right; i++) {
					str = swap(str, left, i);
					permute(str, left + 1, right);
					str = swap(str, left, i);
				}
			}
		}

		function swap(a: string, i: number, j: number): string {
			const charArray = Array.from(a);
			[charArray[i], charArray[j]] = [charArray[j], charArray[i]];
			return charArray.join("");
		}

		permute(str, 0, str.length - 1);
		return permutationList;
	}
</script>

<div class="calculatorBody">
	<Header />
	<NumberInput bind:inputValue onchange={calculatePermutations} />
	{#key permutations}
	<div class="permutations">
		{#each permutations as permutation}
			<PermutationOption {permutation} />
		{/each}
	</div>
	{/key}
	<Footer {currentYear} />
</div>

<style>
	:global(*) {
		-webkit-touch-callout: none; /* iOS Safari */
		-webkit-user-select: none; /* Safari */
		-khtml-user-select: none; /* Konqueror HTML */
		-moz-user-select: none; /* Old versions of Firefox */
		-ms-user-select: none; /* Internet Explorer/Edge */
		user-select: none; /* Non-prefixed version, currently supported by Chrome, Edge, Opera and Firefox */
		font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
		background: #121212;
		color: #eee;
	}

	:global(a) {
		text-decoration: none;
	}

	.calculatorBody {
		text-align: center;
		position: relative;
	}
</style>
