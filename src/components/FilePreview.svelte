<script lang="ts">
    import { createEventDispatcher } from "svelte";
	import { sep } from "@tauri-apps/api/path";

    const dispatch = createEventDispatcher();

    export let key: number;
	export let path: string;

	const split = path.split(sep);
	const fileName = split.at(split.length - 1);

    const dotSplit = path.split(".");
    const fileType = dotSplit.length === 1 ? "" : dotSplit.at(dotSplit.length - 1);
</script>

<style>
	.file-preview {
		display: flex;
		flex-direction: column;
        background-color: #282828;
        border: thick ouset black;
        padding: 10px;
        position: relative;
	}
    img {
        max-width: 10vw;
        max-height: auto;
        display: block;
    }
    .buttons {
        position: absolute;
        top: 0;
        right: 0;
    }
    button {
        /* zanim na mnie nakrzyczycie te kolory zrobię normalnie potem ale mi się nie chce teraz Xd */
        background-color: #3C3836;
        color: #EBDBB2;
        border: none;
        border-radius: 5px;
    }
    button:hover {
        background-color: #504945;
    }
</style>

<div class="file-preview">
    <div class="buttons">
        <button>👁</button>
        <button>✎</button>
        <button on:click={() => dispatch("remove", {})}>🗑</button>
    </div>
    <img src={"asset://" + path} alt={path} />
	<div class="file-info">
		{fileName}; {fileType}
	</div>
</div>
