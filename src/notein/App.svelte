<script>
	import Header from './header/Header.svelte';
	import Body from './body/Body.svelte';
	import { writable } from 'svelte/store';

	/**
	 * @type {Array} 
	 * Хранилище задач
	 */
	let arr = writable([]);

	/**
	 * @type {import('svelte/store').Writable<boolean>}
	 * Хранилище для отслеживания состояния окна
	 */
	let showNote = writable(false);

	/**
	 * @type {import('svelte/store').Writable<any>}
	 * Хранилище для текста задачи
	 */
	let textareaValue = writable('');

	/**
	 * @function
	 * Функция для сброса всех значений в массиве arr в установленное время
	 */
	function resetArr() {
		arr.set([]);
	}

	/**
	 * @function
	 * Функция для установки. Выполняется при нажатии кнопки ADD
	 */
	function openNote() {
		showNote.set(true);
	}

</script>

<Header {resetArr}/>
<Body {openNote} {showNote} {textareaValue} {arr}/>

