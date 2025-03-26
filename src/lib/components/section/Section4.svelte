<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';

	import PosterImage from '$lib/assets/poster.png';

	export let id = '';
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700">SESSION</Text>
	<div id="main-container">
		<img src={PosterImage} alt="map" width="340px" />
		<div id="container">
			<div id="textbox" class="text-with-label-1">
				<Text fontSize="38px" fontWeight="700">학교에서 알려주지 않는 GPT 사용법</Text>
				<Text fontSize="19px" fontWeight="500" color="#A5A5A5">by. 최강민 (해달에듀 대표)</Text>
			</div>
			<div id="textbox" class="text-with-label-2">
				<Text fontSize="26px" fontWeight="600">세션 소개</Text>
				<Text fontSize="16px" fontWeight="400" color="#A5A5A5">
					여기에 세션 소개를 아주아주 멋있고 기이이일게 작성합니다.
					<br />
					여기에 세션 소개를 아주아주 멋있고 기이이일게 작성합니다.
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
</style>
