<script lang="ts">
	import Bar from "$lib/Bar.svelte";
	import Panel from "$lib/Panel.svelte";
	import type { Element } from "$lib/Element";
  	import Todo from "$lib/Todo.svelte";

	let panel: string = "all";
	let inputText: string = "";
	let elements: Element[] = [];

	function addElement() {
		if (inputText == "")
			return ;
		elements.push({id: elements.length, value: inputText, active: false});
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

	<div class="todos">
	{#each elements as element}
		{#if panel == 'all'
			|| (panel == 'active' && !element.active)
			|| (panel == 'completed' && element.active)}
		<Todo bind:element={element} />
		{/if}
	{/each}
	</div>

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

	.todos {
		display: flex;
		flex-direction: column;
		gap: 27px;
		width: 100%;
	}
</style>
