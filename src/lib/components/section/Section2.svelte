<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';

	export let id = '';
</script>

<section {id}></section>

<style>
	section {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100vh;
		background-color: var(--navy);
		box-shadow: 0px 0px 100px 100px var(--navy);
	}

	div {
		display: flex;
		flex-direction: column;
		gap: 30px;
	}

	button {
		border: none;
		outline: none;

		position: absolute;
		bottom: 10%;

		width: 270px;
		height: 60px;
		border-radius: 30px;
		background-color: #031a8d;
	}
</style>
