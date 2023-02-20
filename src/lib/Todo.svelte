<script lang="ts">
	import type { Element } from "./Element";

	export let element: Element;
</script>

<div class="todo">
	<input type="checkbox" bind:checked={element.active} />
	<p class:checked={element.active}>{element.value}</p>
</div>

<style>
	.todo {
		display: flex;
	}

	.checked {
		text-decoration:line-through;
	}
</style>
