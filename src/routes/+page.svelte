<script lang="ts">
	let grid = Array(100)
		.fill([])
		.map(() => Array(100).fill('#fff'));
	let selectedColor = '#000';

	const changeColor = (i: number, j: number) => {
		grid[i][j] = selectedColor;
	}
</script>

<div class="grid">
	{#each grid as row, i}
		{#each row as cell, j}
			<div class="box" style="background-color: {cell}" on:click={() => changeColor(i, j)}></div>
		{/each}
	{/each}
</div>

<div class="color-picker">
	<label for="color">Select color: </label>
	<input type="color" id="color" bind:value={selectedColor} />
</div>

<style>
	.grid {
		display: grid;
		grid-template-columns: repeat(100, 8px);
		grid-template-rows: repeat(100, 8px);
	}
	.box {
		width: 8px;
		height: 8px;
		border: 0px solid #000;
		cursor: pointer;
	}
	.color-picker {
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		padding: 10px;
		background-color: #f0f0f0;
		text-align: center;
	}
</style>
