<script>
	let input = "";
	let valid = true;
	let result;

	$: valid = /^([01 _]+)$/.test(input);

	$: result = input
		.replace(/(\s|_)+/, "")
		.split("")
		.map((c, _) => Number(c))
		.reverse()
		.map((i, j) => i * Math.pow(2, j))
		.reduce((sum, cur) => sum + cur, 0);
</script>

<h1>Binary to Decimal Converter</h1>
<input bind:value={input} />
{#if input == ""}
	<p>Enter a binary number</p>
{:else if valid}
	<p>Result: {result}</p>
{:else}
	<p>Invalid Input</p>
{/if}

<style>
</style>
