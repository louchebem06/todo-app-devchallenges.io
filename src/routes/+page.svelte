<script lang="ts">
	import Bar from "$lib/Bar.svelte";
	import Panel from "$lib/Panel.svelte";
	import type { Element } from "$lib/Element";
  import { element } from "svelte/internal";

	let panel: string = "all";
	let inputText: string = "";
	let elements: Element[] = [];

	function addElement() {
		if (inputText == "")
			return ;
		elements.push({value: inputText, active: false});
		inputText = "";
		elements = elements.slice();
	}
</script>

<svelte:head>
	<title>Todo App</title>
</svelte:head>

<div class="content">

	<h1>#todo</h1>

	<Panel bind:panel={panel} />

	{#if panel != "completed"}
		<Bar fn={addElement} bind:value={inputText}/>
	{/if}

	{#each elements as element}
		{#if panel == 'all'
			|| (panel == 'active' && !element.active)
			|| (panel == 'completed' && element.active)}
		<p>{element.value}</p>
		{/if}
	{/each}

</div>

<style>
	.content {
		display: flex;
		align-items: center;
		flex-direction: column;
		max-width: 608px;
		margin: auto;
	}

	.content h1 {
		font-family: 'Raleway', sans-serif;
		margin-bottom: 58px;
		font-weight: 700;
		font-size: 36px;
		line-height: 42px;
		letter-spacing: -0.045em;
	}
</style>
