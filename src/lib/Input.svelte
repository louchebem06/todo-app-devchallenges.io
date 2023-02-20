<script lang="ts">
	export let value: string;
	export let fn: any;

	function handler(e: any) {
		if (e.key == 'Enter')
			fn();
	}
</script>

<input on:keypress={handler} bind:value={value} type="text" placeholder="add details"/>

<style>
	input {
		font-style: normal;
		font-weight: 400;
		font-size: 14px;
		line-height: 17px;
		color: #828282;
		width: 476px;
		padding: 20px 12px;
		border: 1px solid #BDBDBD;
		border-radius: 12px;
		outline: none;
	}
</style>
