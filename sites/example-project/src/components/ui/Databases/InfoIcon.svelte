<script>
    import IoIosHelpCircleOutline from 'svelte-icons/io/IoIosHelpCircleOutline.svelte'
    import { fade } from 'svelte/transition';

    let visible = false

    const showMessage = () => visible = true
    const hideMessage = () => visible = false
</script>

<span 
    on:focus={showMessage} on:blur={hideMessage}
    on:mouseenter={showMessage} on:mouseleave={hideMessage}
    class="additional-info-icon"
>
    <IoIosHelpCircleOutline/>
    {#if visible}
    <span transition:fade class=info-msg>
        <slot></slot>
    </span>
    {/if}
</span>

<style scoped>
    span.additional-info-icon {
        width: 18px;
        color:var(--grey-600);
        display:inline-block;
        vertical-align: middle;
        line-height: 1em;
        cursor: help;
        position:relative;
        text-transform: none;
    }

    .additional-info-icon .info-msg {
        position: absolute;
        top: -5px;
        left: 105%;
        padding-left: 5px;
        padding-right: 5px;     
        padding-top: 2px;
        padding-bottom: 1px;   
        color: white;
        font-family: sans-serif;
        font-size: 0.8em;
        background-color: var(--grey-900);
        opacity: 0.85;
        border-radius: 6px;
        z-index: 1;
        max-width: 200px;
        min-width: 150px;
    }
</style>