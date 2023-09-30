<script>
	let input = "";
	let valid = true;
	let result;

	$: valid = input
		.split("")
		.reduce((r, cur) => r && /1|0|\s|_/.test(cur), true);

	$: result = input
		.replace(" ", "")
		.replace("_", "")
		.split("")
		.map((c, _) => Number(c))
		.reverse()
		.map((i, j) => i * Math.pow(2, j))
		.reduce((sum, cur) => sum + cur, 0);
</script>

<div>
	<h1>Binary to Decimal Converter</h1>
	<input
		placeholder="Input a Binary Number"
		bind:value={input}
	/>
	{#if valid}
		<p>Result: {result}</p>
	{:else}
		<p>Invalid Input</p>
	{/if}
</div>

<style>
</style>
