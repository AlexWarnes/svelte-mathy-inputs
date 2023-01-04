<script lang="ts">
	interface ValueProp {
		x: number;
		y: number;
		z: number;
		[key: string]: unknown;
	}
	export let groupLabel: string = '';
	export let value: ValueProp;
	export let min: number | undefined = undefined;
	export let max: number | undefined = undefined;
	export let step: number = 1;
	export let style: string = '';

	// TODO: radians prop for automatic step/min/max settings?
</script>

<slot name="group-label">
	<p class="group-label">{groupLabel}</p>
</slot>
<form on:change on:input class="vec-row" {style}>
	<label class="vec3"
		><span>x</span>
		<input class="vec3" type="number" {min} {max} {step} bind:value={value['x']} />
	</label>
	<label class="vec3"
		><span>y</span>
		<input class="vec3" type="number" {min} {max} {step} bind:value={value['y']} />
	</label>
	<label class="vec3"
		><span>z</span>
		<input class="vec3" type="number" {min} {max} {step} bind:value={value['z']} />
	</label>
</form>

<style>
	* {
		box-sizing: border-box;
	}
	input.vec3 {
		display: block;
		width: 3rem;
	}
	.group-label {
		margin: 1rem 0 0.25rem;
	}
	.vec-row {
		width: 100%;
		padding: 0 0.25rem 1rem;
		display: flex;
		flex-flow: row wrap;
		justify-content: space-between;
		align-items: flex-start;
	}
</style>
