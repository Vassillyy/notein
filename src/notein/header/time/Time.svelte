<script>
/**
 * @function
 * @name onMount
 * @memberof module:svelte
 * @type {import("svelte").onMount}
 * @description Импортируем функцию onMount из модуля "svelte"
 */
import { onMount } from "svelte";

/**@description Описание пропса resetArr */
export let resetArr

/**
 * @type {string}
 * @description Переменная хранящая время
 */
let time = '';

/**
 * @function
 * @description Функция для подсчета времени
 */
function sayTime() {
    /**
     * @type {Date}
     * @description Получаем текущую дату
     */
    let now = new Date();

    /**
     * @type {Date}
     * @description Получаем дату завтрашнего дня
     */
    let tomorrow = new Date(now.getFullYear(), now.getMonth(), now.getDate() + 1);

    /**
     * @type {number}
     * @description Вычисляем разницу между завтрашним днем и текущим временем
     */
    let date = tomorrow - now;


    /**
     * @type {number}
     * @description Вычисляем секунды до определенного момента
     */
    let seconds = Math.floor((date / 1000) % 60);

     /**
     * @type {number}
     * @description Вычисляем минуты до определенного момента
     */
    let minutes = Math.floor((date / 1000 / 60) % 60);

    /**
     * @type {number}
     * @description Вычисляем часы до определенного момента
     */
    let hours = Math.floor((date / (1000 * 60 * 60)) % 24);

    /**
     * @type {string}
     * @description Строка с отображением времени до определенного момента
     */
    time = `${hours} : ${minutes} : ${seconds}`;

    /**
     * @description Проверяем, если время равно 00:00:00, то вызываем функцию resetArr()
     */
    if (hours === 0 && minutes === 0 && seconds === 0) {
        /**
         * @function
         * @description Функция для очистки хранилища arr
        */
        resetArr()
    }
}

/**
 * @description Функция для вызова функции sayTime и установки интервала для ее повторного вызова
 */
onMount(() => {
    /**
     * @description Вызываем функцию sayTime при первой загрузке страницы
     */
    sayTime();

     /**
     * @type {number}
     * @description Устанавливаем интервал для вызова функции sayTime каждую секунду
     */
    setInterval(sayTime, 1000);
})

</script>

<div>
    <p>Time until tasks are reset</p>
    <p>{time}</p>
</div>

<style>
    div {
        width: 100%;
    }
    p {
        font-size: 4vw;
        margin: 0;
        text-align: center;
    }
</style>