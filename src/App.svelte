<script lang="ts">
	import ChannelList from "./components/ChannelList.svelte";
	import ChannelView from "./components/ChannelView.svelte";
</script>

<main>
	<div id="app">
		<ChannelList />
		<ChannelView />
	</div>
</main>

<style>
	#app {
		font-family: Inter, Avenir, Helvetica, Arial, sans-serif;
		font-size: 16px;
		line-height: 24px;
		font-weight: 400;	

		color: rgba(235, 219, 178, 1);
		background-color: #282828;
		--foreground: #ebdbb2;
		--background: #282828;	

		font-synthesis: none;
		text-rendering: optimizeLegibility;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		-webkit-text-size-adjust: 100%;	

        display: flex;

        height: 100vh;
        width: 100vw;
	}
</style>
