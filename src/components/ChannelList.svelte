<script lang="ts">
    import { Body, fetch } from "@tauri-apps/api/http";

    export let serverID: string;

    let channels = [];

	(async () => {
        const respone = await fetch("http://127.0.0.1:8000/server/" + serverID, {
            method: "GET", 
        });
        
	})();

</script>

<style>
	.channel-list {
		display: flex;
		flex-direction: column;
	}
</style>

<div class="channel-list">
    {#each channels as channel}
        
    {/each}
</div>
