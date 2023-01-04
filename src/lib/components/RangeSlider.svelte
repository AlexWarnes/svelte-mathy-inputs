<script lang="ts">
	export let value: number;
	export let label: string;
	export let type: 'NORM' | 'NUM' | 'RAD' = 'NUM';
	export let min: number = 0;
	export let max: number = type === 'NORM' ? 1 : type === 'RAD' ? 2 * Math.PI : 1000;
	export let step: number = type === 'NORM' ? 0.01 : type === 'RAD' ? (2 * Math.PI) / 64 : 1;
	export let style: string = '';
</script>

<label {style}
	>{label}
	<input type="range" {min} {max} {step} bind:value on:input on:change />
</label>

<style>
	@import '../styles/forms.css';
</style>
