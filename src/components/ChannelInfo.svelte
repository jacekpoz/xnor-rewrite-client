<script lang="ts">
    export let name: string;
    export let description: string;
</script>

<style>
    .channel-info {
        padding: 10px 20px;
        display: flex;
        flex-direction: column;
        overflow-wrap: break-word;
    }
</style>

<div class="channel-info">
    <h1>#{name}</h1>
    <p>{description}</p>
</div>
