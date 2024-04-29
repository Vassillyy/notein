<script>
	/** @description Описание пропса showNote */
	export let showNote

	/** @description Описание пропса textareaValue */
    export let textareaValue

	/** @description Описание пропса arr */
    export let arr

	/**
	 * @function
	 * @description Функция для обновления хранилища arr, сброса значения хранилища textareaValue
	 * и изменения хранилища showNote на false. Выполняется при нажатии на кнопку Create
	 */
	function addNoteToArr() {
		/**
		 * @description Условие если хранилище textareaValue не является пустой строкой или null
		*/
		if ($textareaValue !== null && $textareaValue !== '') {
			/**
			 * @description Обновление хранилища arr
			*/
			arr.update(arr => [...arr, $textareaValue]);

			/**
			 * @description Сброс значения хранилища textareaValue
			*/
			textareaValue.set('');

			/**
			 * @description Изменениу хранилища showNote на false
			*/
			showNote.set(false);
		}
	} 
	
	/**
	 * @function
	 * @description Функция для сброса значения хранилища textareaValue и изменения хранилища 
	 * showNote на false. Выполняется при нажатии на кнопку Cancel
	 */
	function closeNote() {
		textareaValue.set('');
		showNote.set(false);
	}
	
</script>

{#if $showNote}
	<div class='font'></div>
{/if}

{#if $showNote}
	<div>
		<textarea bind:value={$textareaValue} placeholder="Введите текст"></textarea>
		<span>
			<button on:click={closeNote}>Cancel</button>
			<button  on:click={addNoteToArr}>Create</button>
		</span>
	</div>
{/if}

<style>
    div {
        margin: 0 auto;
		width: 60%;
		height: 50%;
		border-radius: 3vw;
		border: 0.5vw solid LightSlateGray;
		position: absolute;
		top: 25%;
		left: 20%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		background-color: MistyRose;  
		z-index: 100;
		overflow: hidden;
    }
    textarea {
		border: none;
		outline: none;
		font-size: 3vw;
		padding: 2vw;
		width: 100%; 
		height: 70%;
		resize: none;
		border-radius: 3vw 3vw 0 0;
		background-color: MistyRose;
   	}
  	textarea::-webkit-scrollbar {
		width: 5px; 
	}
	textarea::-webkit-scrollbar-track {
		background: MistyRose; 
	}

	textarea::-webkit-scrollbar-thumb {
		background-color: MistyRose; 
		border-radius: 20px; 
		border: 3px solid MistyRose; 
	}
    button {
	    width: 10vw;
		height: 6vh;
		border-radius: 1vw;
		border: 0.1vw solid black;
		background-color: LavenderBlush;
		margin: 1vw 2vw;
		font-size: 2vw;
  	}
	span {
		display: flex;
		justify-content: center;
	}
	.font {
		width: 100%;
		height: 100%;
		position: fixed;
		top: 0;
		left: 0;
		background-color: DarkGray;
		z-index: 99;
		border: none;
		border-radius: 0;
	}
</style>