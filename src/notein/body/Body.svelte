<script>
    import Items from './itemsAdd/Items.svelte' 
    import Window from './window/Window.svelte';

    /** @description Описание пропса showNote */
    export let showNote

    /** @description Описание пропса textareaValue */
    export let textareaValue

    /** @description Описание пропса arr */
    export let arr

    /** @description Описание пропса openNote */
    export let openNote
    
</script>


<Items {openNote} {arr}/>
<Window {showNote} {textareaValue} {arr}/>

