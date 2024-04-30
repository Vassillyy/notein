<script>
import { onMount } from "svelte";

/** Описание пропса resetArr */
export let resetArr

/**
 * @type {string}
 * Переменная хранящая время
 */
let time = '';

/**
 * @function
 * Функция для подсчета времени
 */
function sayTime() {
    let now = new Date();
    let tomorrow = new Date(now.getFullYear(), now.getMonth(), now.getDate() + 1);
    let date = tomorrow - now;

    let seconds = Math.floor((date / 1000) % 60);
    let minutes = Math.floor((date / 1000 / 60) % 60);
    let hours = Math.floor((date / (1000 * 60 * 60)) % 24);

    time = `${hours} : ${minutes} : ${seconds}`;

    if (hours === 0 && minutes === 0 && seconds === 0) {
        resetArr()
    }
}

/** Функция для вызова функции sayTime и установки интервала для ее повторного вызова */
onMount(() => {
    sayTime();
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