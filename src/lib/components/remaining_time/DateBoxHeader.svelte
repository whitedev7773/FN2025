<script lang="ts">
	import Text from '$lib/components/Text.svelte';

	export let text: string = '';
</script>

<div>
	<Text fontSize="14px" fontWeight="600" textAlign="center" disable_animation={true}>
		{text}
	</Text>
</div>

<style>
	div {
		position: relative;
		z-index: 10;

		width: 100%;
		height: 34px;

		display: flex;
		justify-content: center;
		align-items: center;

		background-color: #50b97d;
	}
</style>
