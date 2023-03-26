<script lang="ts">
    import Modal from "./Modal.svelte";
    import ChannelInfo from "./ChannelInfo.svelte";

	export let name: string;
	export let description: string;

    let showChannelInfo: boolean = false;

    const toggle = () => showChannelInfo = !showChannelInfo;
</script>

<style>
	.channel-header {
		display: flex;
		flex-direction: row;
        padding: 10px;
	}
	.channel-name {
		font-size: 20px;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
        user-select: none;
        -webkit-user-select: none;
        cursor: default;
	}
	.channel-description {
        flex: 1;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
        user-select: none;
        -webkit-user-select: none;
        cursor: default;
        margin-left: 10px;
	}
    .divider {
        width: 2px;
        margin: 6px 0;
        background: #EBDBB2;
    }
</style>

<div class="channel-header">
	<div class="channel-name">#{name}</div>
    <div class="divider" />
	<div class="channel-description" on:click={toggle}>{description}</div>
</div>

{#if showChannelInfo}
    <Modal bind:visible={showChannelInfo}>
        <ChannelInfo {name} {description} />
    </Modal>
{/if}
