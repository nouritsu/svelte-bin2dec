<script lang="ts">
	let input: string = "";
	let valid = true;
	let result: number;

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
{#if !input}
	<p>Enter a binary number</p>
{:else if valid}
	<p>Result: {result}</p>
{:else}
	<p>Invalid Input</p>
{/if}

<style>
	h1 {
		text-align: center;
		font-size: 2rem;
		transform: translate();
	}

	input {
		text-align: center;
		width: 100%;
		font-size: 1.5rem;
	}

	p {
		text-align: center;
		font-size: 1.5rem;
	}
</style>
