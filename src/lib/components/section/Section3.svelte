<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';
	import BoxedMessage from './section3/BoxedMessage.svelte';

	export let id = '';
</script>

<section {id}>
	<div id="first-line">
		<Text className="shadow-for-dark" fontSize="86px" fontWeight="700" disable_animation={true}
			>함수달은</Text
		>
		<BoxedMessage />
		<Text className="shadow-for-dark" fontSize="60px" fontWeight="400" disable_animation={true}
			>까지</Text
		>
	</div>
	<div id="second-line">
		<Text
			className="shadow-for-dark"
			fontSize="86px"
			fontWeight="700"
			style="
				background: linear-gradient(90deg, #7FF8FC 0%, #2ECC71 100%);
				background-clip: text;
				-webkit-background-clip: text;
				color: transparent;"
		>
			여러분과 함께해요
		</Text>
	</div>
</section>

<style>
	section {
		width: 100%;
		height: 100vh;
		box-sizing: border-box;
		padding: 0 100px;

		position: relative;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 21px;

		background-color: #00000077;
	}

	div {
		box-sizing: border-box;
		width: 100%;
		max-width: 1280px;
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	div#first-line {
		justify-content: flex-start;
		gap: 20px;
	}

	div#second-line {
		justify-content: flex-end;
	}
</style>
