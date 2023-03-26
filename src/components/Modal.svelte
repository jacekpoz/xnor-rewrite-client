<script lang="ts">
    import { fade, scale } from "svelte/transition";

    export let visible: boolean;

    const toggle = () => visible = !visible; 
</script>

<style>
    .modal {
        background-color: rgba(0, 0, 0, 0.7);
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .content {
        background-color: #282828;
        color: #EBDBB2;
        width: 50vw;
        height: 25vh;
        border-radius: 10px;
        box-shadow: 5px 5px #1D2021;
        overflow: hidden;
        position: relative;
    }
    .close {
        border: none;
        background-color: #282828;
        color: #EBDBB2;
        cursor: pointer;
        position: absolute;
        top: 0;
        right: 0;
    }
</style>

<div on:click|self={toggle} class="modal" transition:fade>
    <div class="content" transition:scale>
        <button class="close" on:click={toggle}>x</button>
        <slot></slot>
    </div>
</div>
