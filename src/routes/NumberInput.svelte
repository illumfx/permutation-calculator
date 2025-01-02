<script lang="ts">
	let { inputValue = $bindable(), ...props } = $props();
</script>

<div class="input">
	<input
		bind:value={inputValue}
		{...props}
		type="text"
		pattern="[0-9]"
		name="numberInput"
		id="numberInput"
		maxlength="4"
	/>
</div>

<style>
	input {
		border: solid 2px;
		border-radius: 10px;
		text-align: center;
	}
</style>
