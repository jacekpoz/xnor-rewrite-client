<script lang="ts">
	export let content: string;
	export let time: number;
</script>

<style>
	.message {
		border: thick outset black;
		padding: 5px;
		text-align: left;
        display: flex;
        flex-direction: row;
	}

</style>

<div class="message">
    <div class="profile-picture">
    </div>
    <div class="the-rest">
        <div class="name-and-date">
        </div>
        <div class="content">
            {content}
        </div>
    </div>
</div>
