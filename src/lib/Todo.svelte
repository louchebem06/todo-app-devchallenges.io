<script lang="ts">
	import type { Element } from "./Element";

	export let element: Element;
	export let panel: string;
	export let rmFn: any;

	let checkbox: any;

	function toggle() {
		checkbox.checked = !checkbox.checked;
		element.active = checkbox.checked;
	}
</script>

<div class="mainTodo">
	<div class="todo">
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<span on:click={toggle} class="material-symbols-outlined">
			check
		</span>
		<input bind:this={checkbox} type="checkbox" bind:checked={element.active} />
		<p class:checked={element.active}>{element.value}</p>
	</div>

	{#if panel == "completed"}
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<span on:click={rmFn(element.id)} class="material-symbols-outlined">
			delete
		</span>
	{/if}
</div>

<style>
	.mainTodo {
		display: flex;
		justify-content: space-between;
		color: #BDBDBD;
	}

	.mainTodo span.material-symbols-outlined {
		cursor: pointer;
		user-select: none;
	}

	.todo {
		display: flex;
		gap: 8px;
		align-items: center;
		position: relative;
		user-select: none;
	}

	.todo .material-symbols-outlined {
		position: absolute;
		left: 1px;
		top: 1px;
		z-index: 1;
		color: white;
		cursor: pointer;
	}

	.checked {
		text-decoration:line-through;
	}

	.todo p {
		font-weight: 500;
		font-size: 18px;
		line-height: 22px;
		color: #000000;
	}

	.todo input[type='checkbox'] {
		position: relative;
		cursor: pointer;
		width: 24px;
		height: 24px;
		visibility: hidden;
	}

	.todo input:after {
		content: " ";
		height: 24px;
		width: 24px;
		left: 0;
		top: 0;
		position: absolute;
		border: 1px solid #828282;
		border-radius: 4px;
		visibility: visible;
	}

	.todo input:checked::after {
		background-color: #2F80ED;
	}

	.todo input:checked {
    	background-color: gray;
	}
</style>
