<script lang="ts">
	import ButtonAdd from "./ButtonAdd.svelte";
	import Input from "./Input.svelte";
	
	export let fn: any;
	export let value: string;
</script>

<div class="bar">
	<Input {fn} bind:value={value} />
	<ButtonAdd {fn} />
</div>

<style>
	.bar {
		display: flex;
		gap: 25px;
		width: 100%;
		align-items: center;
		margin-bottom: 33px;
	}
</style>
