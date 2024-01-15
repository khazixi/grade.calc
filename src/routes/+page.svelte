<script>
	import Switch from '$lib/ui/switch/switch.svelte';
	import Label from '$lib/ui/label/label.svelte';
	import '../app.css';

	let checked = false;
	let abc = '';
	let quiz = [0, 0, 0];

	$: grade = checked
		? (quiz.reduce((a, b) => a + b) - Math.min(...quiz)) / 2
		: quiz.reduce((a, b) => a + b) / 3;
</script>

<h1>Grade.calc</h1>

<h2>All in One</h2>
<p>
	<b>Grade.calc</b> provides all the features necessary for calculating your grade for the class.
</p>

<form>
	<div class="inline-flex items-center space-x-2">
		<Switch name="drop" bind:checked />
		<Label for="drop">Drop Lowest</Label>
	</div>
	<p>{checked}</p>
	<br />
	<input type="number" bind:value={quiz[0]} min="0" max="100" />
	<br />
	<input type="number" bind:value={quiz[1]} min="0" max="100" />
	<br />
	<input type="number" bind:value={quiz[2]} min="0" max="100" />
	<br />

	<p>
		{grade}
	</p>
</form>
