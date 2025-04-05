<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';

	export let id = '';
</script>

<section {id}>
	<div id="title" class="shadow-for-dark">
		<Text fontSize="128px" fontWeight="900" textAlign="center" mobileFontSize="70px"
			><span style="color: var(--dark-green)">FN</span> 2025</Text
		>
		<Text fontSize="40px" fontWeight="400" textAlign="center" mobileFontSize="24px"
			>함수달이 준비한 첫번째 세미나</Text
		>
	</div>
	<a
		class="shadow-for-dark"
		href="https://docs.google.com/forms/d/10d30iOI2bHDYqljQaq73zVONoJHoEGp7UIdbnCkpdWs/edit"
		target="_blank"
	>
		<Text
			color="white"
			fontSize="24px"
			fontWeight="400"
			textAlign="center"
			mobileFontSize="20px"
			style="text-decoration: none;"
			disable_animation={true}>참가 신청하기</Text
		>
	</a>
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
		align-items: center;
		gap: 30px;
	}

	a {
		border: none;
		outline: none;
		text-decoration: none;

		position: absolute;
		z-index: 10;
		bottom: 10%;

		display: flex;
		justify-content: center;
		align-items: center;

		width: 270px;
		height: 60px;
		border-radius: 30px;
		background-color: #031a8d;
	}

	@media (max-width: 1000px) {
		div {
			gap: 10px;
		}

		a {
			width: 200px;
			height: 50px;
			border-radius: 25px;
		}
	}
</style>
