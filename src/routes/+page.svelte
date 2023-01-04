<script lang="ts">
	import RangeSlider from '$lib/components/RangeSlider.svelte';
	import RotationSliders from '$lib/components/RotationSliders.svelte';
import Vec3Input from '$lib/components/Vec3Input.svelte';

	let v3 = { x: 1, y: 2, z: 3 };
  let rotationV3 = { x: Math.PI, y: Math.PI / 2, z: 0 }

  let rotation = Math.PI / 2;
  let norm = 0.25;
  let num = 5;

</script>

<form action="#">
  <h2>{'<Vec3Input />'}</h2>
	<Vec3Input bind:value={v3} groupLabel="Vec3 Input" />
	<pre>{JSON.stringify(v3, null, 2)}</pre>
</form>
<form>
  <h2>{'<RangeSlider />'}</h2>
  <RangeSlider bind:value={rotation} label="RAD" type="RAD"/>
	<pre>{JSON.stringify(rotation, null, 2)}</pre>
  <RangeSlider bind:value={norm} label="NORM" type="NORM"/>
	<pre>{JSON.stringify(norm, null, 2)}</pre>
  <RangeSlider bind:value={num} label="NUM (Default)" type="NUM"/>
	<pre>{JSON.stringify(num, null, 2)}</pre>
</form>
<form>
	<h2>{'<RotationSliders />'}</h2>
	<p style="margin: 0; font-size: 0.875rem;">(values in radians)</p>
	<RotationSliders bind:value={rotationV3} groupLabel="Default" />
	<RotationSliders bind:value={rotationV3} groupLabel="Style Prop" style="gap: 0.5rem; padding: 0.875rem;" />
	<RotationSliders bind:value={rotationV3}>
		<h3 slot="group-label">Slot Label <span>&#128640;</span></h3>
	</RotationSliders>
	<pre>{JSON.stringify(rotationV3, null, 2)}</pre>
</form>

<style>
	:global(body) {
		font-family: sans-serif;
	}

	form {
		max-width: 320px;
		margin: 1rem auto;
		background-color: royalblue;
		border-radius: 0.5rem;
		color: white;
		padding: 1rem;
	}
</style>
