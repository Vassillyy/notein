<script>
    import Items from './itemsAdd/Items.svelte' 
    import Window from './window/Window.svelte';

    /** Описание пропса showNote */
    export let showNote

    /** Описание пропса textareaValue */
    export let textareaValue

    /** Описание пропса arr */
    export let arr

    /** Описание пропса openNote */
    export let openNote
    
</script>


<Items {openNote} {arr}/>
<Window {showNote} {textareaValue} {arr}/>

