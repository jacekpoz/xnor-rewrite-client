<script lang="ts">
	import Message from "./Message.svelte";

	let messages = [];
	export const addMessage = (message: string) => messages = [...messages, message];
</script>

<style>
	.message-area {
		display: flex;
		flex-direction: column;
		flex-grow: 10;
	}
</style>

<div class="message-area">
	{#each messages as message}
		<Message content={message} time={Date.now()} />
	{/each}
</div>
