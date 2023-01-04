<script lang="ts">
	import RangeSlider from '$lib/components/RangeSlider.svelte';

	interface ValueProp {
		x: number;
		y: number;
		z: number;
		[key: string]: unknown;
	}
	export let groupLabel: string = '';
	export let value: ValueProp;
	export let min: number = Math.PI * -2;
	export let max: number = Math.PI * 2;
	export let step: number = (2 * Math.PI) / 64;
	export let style: string = '';
	// TODO: radians prop for automatic step/min/max settings
</script>

<slot name="group-label">
	<p class="group-label">{groupLabel}</p>
</slot>
<form on:change on:input class="vec-row" {style}>
	<RangeSlider
		bind:value={value.x}
		label="x"
		type="RAD"
		{min}
		{max}
		{step}
		style="display: block;"
	/>
	<RangeSlider
		bind:value={value.y}
		label="y"
		type="RAD"
		{min}
		{max}
		{step}
		style="display: block;"
	/>
	<RangeSlider
		bind:value={value.z}
		label="z"
		type="RAD"
		{min}
		{max}
		{step}
		style="display: block;"
	/>
</form>

<style>
	* {
		box-sizing: border-box;
	}
	.group-label {
		margin: 1rem 0 0.25rem;
	}
	.vec-row {
		width: 100%;
		padding: 0 0.25rem 1rem;
		display: flex;
		flex-flow: column;
		justify-content: flex-start;
		align-items: flex-start;
	}
</style>
