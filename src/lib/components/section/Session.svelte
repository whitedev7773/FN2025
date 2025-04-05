<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';

	import PosterImage from '$lib/assets/poster.png';

	export let id = '';
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">SESSION</Text>
	<div id="main-container">
		<img src={PosterImage} alt="map" width="327px" />
		<div id="container">
			<div id="textbox" class="text-with-label-1">
				<Text fontSize="38px" fontWeight="700" mobileFontSize="20px"
					>학교에서 알려주지 않는 GPT 사용법</Text
				>
			</div>
			<div id="textbox" class="text-with-label-2">
				<Text fontSize="16px" fontWeight="400" color="#A5A5A5" mobileFontSize="13px">
					모두가 GPT를 사용하는 세상에서 어떻게 살아나가야 할까요?
					<br />
					GPT가 말을 듣게 할 수 있는 총알을 여러분들에게 나눠드릴게요.
				</Text>
			</div>
		</div>
	</div>
</section>

<style>
	section {
		width: 100%;
		box-sizing: border-box;
		padding: 300px 0;

		position: relative;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 100px;

		background-color: var(--navy);
	}

	#main-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		gap: 50px;
	}

	img {
		border-radius: 10px;
	}

	#container {
		display: flex;
		flex-direction: column;
		gap: 40px;
	}

	#textbox {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		gap: 10px;
	}

	@media (max-width: 1000px) {
		section {
			padding: 100px 0;
		}

		#main-container {
			flex-direction: column;
			gap: 20px;
		}

		img {
			width: 200px;
		}

		#container {
			gap: 10px;
			box-sizing: border-box;
			padding: 20px;
		}
	}
</style>
