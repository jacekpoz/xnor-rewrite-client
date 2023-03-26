<script lang="ts">
    import { ulid } from "ulid";
    import { Body, fetch } from "@tauri-apps/api/http";
	import ChannelHeader from "./ChannelHeader.svelte";
	import MessageArea from "./MessageArea.svelte";
	import MessageBox from "./MessageBox.svelte";

	let area: MessageArea;

	const sendMessage = async (message: string) => {
		area.addMessage(message);
        await fetch("http://127.0.0.1:8000/message", {
            method: "POST", 
            body: Body.json({
                message_id: ulid(), 
                author_id: "AID", 
                chat_id: "CID", 
                content: message
            })
        });
	};

    let channelName = "kanał";
    let channelDescription = "jiounhjsdf adpsfafpfsdpa sfdknlvlndjfvnla nwejlfkawnlewcbn ejcfkwlaecbflkwabcfljw aebxfljwbfxjhebxwej hwlbxsfldjnfljklnf dsflawcejlfnljkcef nljkwanefcnawec";
</script>

<style>
	.channel-view {
		display: flex;
		flex-direction: column;
	}
</style>

<div class="channel-view">
	<ChannelHeader name={channelName} description={channelDescription} />
	<MessageArea bind:this={area} />
	<MessageBox 
        on:sendMessage={ (ev) => sendMessage(ev.detail.message) }
        channelName={channelName} />
</div>
