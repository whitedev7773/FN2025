<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';
	import BoxedMessage from '$lib/components/section/Brand/BoxedMessage.svelte';

	export let id = '';
</script>

<section {id}>
	<div id="first-line">
		<Text
			className="shadow-for-dark"
			fontSize="clamp(40px, 5vw, 85px)"
			fontWeight="700"
			disable_animation={true}
			mobileFontSize="46px">함수달은</Text
		>
		<BoxedMessage />
		<Text
			className="shadow-for-dark"
			fontSize="clamp(26px, 2.5vw, 45px)"
			fontWeight="400"
			disable_animation={true}
			mobileFontSize="40px">까지</Text
		>
	</div>
	<div id="second-line">
		<Text
			className="shadow-for-dark"
			fontSize="clamp(40px, 5vw, 85px)"
			fontWeight="700"
			mobileFontSize="46px"
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

	/* 모바일일 땐 모두 세로로 정렬 */
	@media (max-width: 1000px) {
		section {
			padding: 0 20px;
		}

		div {
			flex-direction: column;
			justify-content: center;
			align-items: center;
			gap: 10px;
		}

		div#first-line {
			justify-content: center;
			gap: 10px;
		}

		div#second-line {
			justify-content: center;
		}
	}
</style>
