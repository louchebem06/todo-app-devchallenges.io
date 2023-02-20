<script lang="ts">
	export let fn: any;
</script>

<button on:click={fn}>add</button>

<style>
	button {
		font-style: normal;
		font-weight: 600;
		font-size: 14px;
		line-height: 17px;
		color: #FFFFFF;
		width: 109px;
		height: 56px;
		background: #2F80ED;
		box-shadow: 0px 2px 6px rgba(127, 177, 243, 0.4);
		border-radius: 12px;
		border: none;
		cursor: pointer;
	}	
</style>
