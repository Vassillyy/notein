<script>
	import Header from './header/Header.svelte';
	import Body from './body/Body.svelte';

	/**
	 * @function
	 * @name writable
	 * @memberof module:svelte/store
	 * @type {import('svelte/store').writable}
	 * @description Импорт функции writable из модуля 'svelte/store'
	 */
	import { writable } from 'svelte/store';

	/**
	 * @type {Array} 
	 * @description Хранилище задач
	 */
	let arr = writable([]);

	/**
	 * @type {import('svelte/store').Writable<boolean>}
	 * @description Хранилище для отслеживания состояния окна
	 */
	let showNote = writable(false);

	/**
	 * @type {import('svelte/store').Writable<any>}
	 * @description Хранилище для текста задачи
	 */
	let textareaValue = writable('');

	/**
	 * @function
	 * @description Функция для сброса всех значений в массиве arr в установленное время
	 */
	function resetArr() {
		arr.set([]);
	}

	/**
	 * @function
	 * @description Функция для установки. Выполняется при нажатии кнопки ADD
	 */
	function openNote() {
		showNote.set(true);
	}

</script>

<Header {resetArr}/>
<Body {openNote} {showNote} {textareaValue} {arr}/>

