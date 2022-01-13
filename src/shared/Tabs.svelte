<script>
    export let items,activeItem
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher()
</script>

<div class="tabs">
    <ul>
        {#each items as item}
            <li on:click={()=>dispatch('tabChange',item)}>
                <div class:active={item === activeItem}>{item}</div>
            </li>
        {/each}
    </ul>
</div>

<style>
    .active {
        color: whitesmoke;
        border: 1.5px solid cornflowerblue;
        padding: 8px;
        background-color: cornflowerblue;
        border-radius: 3px;
    }

    ul {
        display: flex;
        list-style-type: none;
        justify-content: center;
        padding: 0;
    }

    .tabs {
        margin-bottom: 40px;
    }

    li {
        margin: 0 16px;
        cursor: pointer;
    }
</style>