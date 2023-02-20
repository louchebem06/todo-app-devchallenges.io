<script lang="ts">
	export let panel: string;
</script>

<div class="panel">
	<button on:click={() => { panel = 'all' }} class:active={panel == 'all'}>All</button>
	<button on:click={() => { panel = 'active' }} class:active={panel == 'active'}>Active</button>
	<button on:click={() => { panel = 'completed' }} class:active={panel == 'completed'}>Completed</button>
</div>

<style>
	.panel {
		display: flex;
		width: 608px;
		border-bottom: 1px solid #BDBDBD;
		padding-bottom: 18px;
		justify-content: space-around;
		margin-bottom: 18px;
	}

	.panel button {
		border: none;
		background-color: transparent;
		cursor: pointer;
		position: relative;
		user-select: none;
		width: 25%;
		font-weight: 600;
		font-size: 14px;
		line-height: 17px;
		color: #333333;
	}

	.panel button.active::after {
		content: " ";
		width: 89px;
		height: 4px;
		background-color: #2F80ED;
		border-radius: 4px 4px 0px 0px;
		position: absolute;
		bottom: -18px;
		left: 50%;
		transform: translate(-50%);
	}
</style>
