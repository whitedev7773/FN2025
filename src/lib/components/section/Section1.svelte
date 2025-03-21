<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';

	export let id = '';
</script>

<section {id}>
	<div id="title" class="shadow-for-dark">
		<Text fontSize="128px" fontWeight="900" textAlign="center"
			><span style="color: var(--dark-green)">FN</span> 2025</Text
		>
		<Text fontSize="40px" fontWeight="400" textAlign="center">함수달이 준비한 첫번째 세미나</Text>
	</div>
	<button class="shadow-for-dark">
		<Text color="white" fontSize="24px" fontWeight="400" textAlign="center">참가 신청하기</Text>
	</button>
</section>

<style>
	section {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100vh;
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
		z-index: 10;
		bottom: 10%;

		width: 270px;
		height: 60px;
		border-radius: 30px;
		background-color: #031a8d;
	}
</style>
