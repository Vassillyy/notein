<script>
  	import { derived, writable } from 'svelte/store';

	/** Описание пропса arr */
	export let arr

	/** Описание пропса openNote */
    export let openNote

	/**
	 * @function
	 * @param {number} index - Индекс массива
	 * Функция для удаления елемента по его индексу из хранилища arr  
	 */
	function removeItem(index) {
		arr.update(items => items.filter((item, i) => i !== index))
	}
	
	let countItems = derived(arr, $arr => $arr.length);
	let countActivItems = derived(arr, $arr => $arr.filter(item => item.checked).length);

</script>

{#if $arr.length > 0}
	<div class="count">{$countActivItems + ' / ' + $countItems}</div>
{/if}

<div class="container">
	{#if $arr.length === 0}
		<p>Create tasks for today</p>
		{:else} 
		<ul>
			{#each $arr as item, i}
			<li>
				<div>
					<button class="remove" on:click={() => removeItem(i)}>remove</button>
					<input type="checkbox" bind:checked={item.checked}>
					<span>{item.text[0].toUpperCase() + item.text.slice(1)}</span>
				</div>
			</li>
			{/each}
		</ul>
	{/if}

	<div>
		<button class="add" on:click={openNote}>ADD</button>
	</div>
</div>

<style>
	 .container {
		width: 100%;
		min-height: 100vh;
		background-color: BlanchedAlmond;
		position: relative;
	}
	p {
		font-size: 5vw;
		font-style: italic;
		margin: 5vw;
		padding: 0;
	}
	ul {
		margin: 3vw;
		padding: 0;
		list-style-type: none;
		width: 85%;
		padding-bottom: 5vh;
	}
	span {
		margin-left: 2vw;
		width: 80%;
		word-wrap: break-word;
		font-style: italic;
		font-size: 5vw;
	}
	div {
		display: flex;
		justify-content: flex-start;
		align-items: flex-start;
	} 
	input {
		width: 4vw;
		height: 4vh;
		margin-left: 2vw;
		margin-top: 5vh;
	}
	input:checked ~ span{
		text-decoration: line-through;
		color: gray;
	}
	.remove {
		border: 0.2vw solid gray;
		border-radius: 2vw;
		width: 6vw;
		height: 5vh;
		background-color: NavajoWhite;
		font-size: 1vw;
		margin-left: 2vw;
		margin-top: 4vh;
	}
	.remove:active {
 		transform: scale(0.95); 
	} 
	.add {
		width: 6vw;
		height: 6vw;
		text-align: center;
		border-radius: 50%;
		border: 3% solid black;
		position: fixed;
		bottom: 5%;
		right: 3%;
		background-color: NavajoWhite;
		font-size: 2vw;
		font-weight: 600;
	}
	.add:active {
 		transform: scale(0.95); 
	} 
	.count {
		background-color: BlanchedAlmond;
		font-size: 4vw;
		font-style: italic;
		padding: 0 0 0 6vw;
		margin: 0;
	}
	svg,
	.redact {
		width: 3vw;
		height: 3vh;
	}
	.redact {
		background-color: NavajoWhite;
		border-radius: 2vw;
		border: 0.05vw solid gray;
		margin-top: 5vh;
	}
	.redact:active {
 		transform: scale(0.95); 
	} 
</style>


