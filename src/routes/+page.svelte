<script>
	import Switch from '$lib/ui/switch/switch.svelte';
	import Label from '$lib/ui/label/label.svelte';
	import '../app.css';

	let checked = false;
	let quiz = [0, 0, 0];

	$: grade = checked
		? (quiz.reduce((a, b) => a + b) - Math.min(...quiz)) / (quiz.length - 1)
		: quiz.reduce((a, b) => a + b) / quiz.length;
</script>

<main class="p-2">
	<h1>Grade.calc</h1>

	<h2>All in One</h2>
	<p>Grade.calc provides all the features necessary for calculating your grade for the class.</p>

	<h2>Sharable</h2>
	<p>Grade.calc enables you to make grade calculating templates to share to all of your friends.</p>

	<h2>Private</h2>
	<p>The grades you enter into your template are yours, and won't be saved to a server.</p>

	<form class="p-2 border rounded w-fit flex flex-col space-y-1">
		<div class="inline-flex items-center space-x-2">
			<Switch name="drop" bind:checked />
			<Label for="drop">Drop Lowest</Label>
		</div>
		<input class="border p-1 rounded-sm" type="number" bind:value={quiz[0]} min="0" max="100" />
		<input class="border p-1 rounded-sm" type="number" bind:value={quiz[1]} min="0" max="100" />
		<input class="border p-1 rounded-sm" type="number" bind:value={quiz[2]} min="0" max="100" />

		<p class="border p-1 rounded-sm">
			{grade}
		</p>
	</form>
</main>
