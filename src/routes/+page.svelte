<script lang="ts">
	import Bar from "$lib/Bar.svelte";
	import Panel from "$lib/Panel.svelte";
	import type { Element } from "$lib/Element";
  	import Todo from "$lib/Todo.svelte";
  import { element } from "svelte/internal";

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

	function removeElement(id: number) {
		elements = elements.filter(element => element.id != id);
	}

	function removeAll() {
		elements = [];
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
			<Todo
				bind:element={element}
				bind:panel={panel}
				rmFn={removeElement}/>
			{/if}
		{/each}
		{#if panel == 'completed'}
		<div class="buttonDelete">
			<button on:click={removeAll}>
				<span class="material-symbols-outlined">
					delete
				</span>
				delete all
			</button>
		</div>
		{/if}
	</div>

</div>

<div class="signature">
	<p>created by <a href="https://github.com/louchebem06">louchebem06</a> - devChallenges.io</p>
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

	.buttonDelete {
		display: flex;
		justify-content: flex-end;
	}

	.todos button {
		font-weight: 600;
		font-size: 12px;
		line-height: 15px;
		color: #FFFFFF;
		background: #EB5757;
		border-radius: 4px;
		border: none;
		width: 124px;
		height: 40px;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 5.5px;
		cursor: pointer;
	}

	.signature {
		position: absolute;
		bottom: 24px;
		left: 0;
		text-align: center;
		width: 100%;
	}

	.signature p, .signature a{
		font-weight: 500;
		font-size: 14px;
		line-height: 17px;
		text-align: center;
		color: #A9A9A9;
	}

	.signature a {
		font-weight: 700;
	}
</style>
