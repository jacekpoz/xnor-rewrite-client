<script lang="ts">
	import { open } from "@tauri-apps/api/dialog";
	import { homeDir } from "@tauri-apps/api/path";
	import { createEventDispatcher } from "svelte";

	import FilePreview from "./FilePreview.svelte";

	const dispatch = createEventDispatcher();

	export let message = "";
    export let channelName: string;

	const isEmpty = (str: string) => !str.trim().length;

	function sendMessage() {
		if (!isEmpty(message)) {
			dispatch("sendMessage", { message });
			message = "";
		}
	}

	const onKeyType = (event: KeyboardEvent) => {
		if (event.key == "Enter" && !event.shiftKey) {
			event.preventDefault();
			sendMessage();
		}
	};

	let files = [];

	const pickFiles = async () => {
		const selected = await open({
			directory: false, 
			multiple: true, 
			defaultPath: await homeDir(), 
		});
        if (selected === null) 
            return;
		for (const file of selected.toString().split(",")) {
            // when someone adds the same file twice we need a key to differentiate them
			files = [...files, { key: Math.random() * 1000 + Date.now(), file }];
		}
	};

</script>

<style>
	.message-box {
		display: flex;
		flex-direction: column;
		background-color: #ebdbb2;
        width: 100vw;
	}
	.file-previews {
		display: flex;
		flex-direction: row;
	}
	.bottom-bar {
		display: flex;
		flex-direction: row;
        justify-content: space-between;
        align-content: stretch;
	}
	textarea {
		background-color: #ebdbb2;
		resize: none;
		outline: none;
		border: none;
		overflow: auto;
        flex: 1;
	}
	button {
		background-color: #ebdbb2;
		border: none;
	}
	button:hover {
		background-color: #fbf1c7;
		border: none;
	}
</style>

<div class="message-box">
	<div class="file-previews">
		{#each files as file}
			<FilePreview 
                bind:key={file.key}
                bind:path={file.file} 
                on:remove={() => files = files.filter(f => f.key != file.key)} />
		{/each}
	</div>
	<div class="bottom-bar">
		<button class="file" on:click={pickFiles}>file</button>
		<textarea 
            on:keypress={onKeyType} 
            bind:value={message} 
            placeholder={"message #" + channelName} />		
		<button class="send" on:click={sendMessage}>send</button>
	</div>
</div>
