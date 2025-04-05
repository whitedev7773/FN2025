<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';
	import LecturerImage from '$lib/assets/lecturer_image.png';

	export let id = '';

	const list = [
		'경북대 전자공학부 졸업',
		'2024 해커그라운드 해커톤 총괄(후원 의성군, Microsoft)',
		'2023 우분투아시아 컨퍼런스 기조연설자',
		'2022 GDG Daegu Devfest 총괄(후원 대구상공회의소, Google)',
		'2022 청년창업사관학교 12기 졸업',
		'2021 대구경북 우수중소벤처기업 우수상',
		'2020 경북대학교 데이터분석 외래교수',
		'2019 KNU 코드페어 총괄(후원 LINE, AWS, 군월드)'
	];
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">LECTURER</Text>
	<div id="main-container">
		<img src={LecturerImage} alt="lecturer" />
		<div id="container">
			<div id="textbox" class="text-with-label-1">
				<Text fontSize="20px" fontWeight="400" mobileFontSize="16px"
					>(주)해달프로그래밍 대표이사</Text
				>
				<Text fontSize="38px" fontWeight="700" mobileFontSize="24px">최강민</Text>
			</div>
			<div id="textbox" class="text-with-label-2">
				{#each list as item}
					<Text fontSize="16px" fontWeight="400" color="#A5A5A5" mobileFontSize="13px">
						{item}
					</Text>
				{/each}
			</div>
		</div>
	</div>
</section>

<style>
	section {
		width: 100%;
		box-sizing: border-box;
		padding: 300px 0;
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
		align-items: flex-start;
		gap: 50px;
		max-width: 900px;
		width: 90%;
	}

	img {
		width: 260px;
		border-radius: 10px;
		flex-shrink: 0;
	}

	#container {
		display: flex;
		flex-direction: column;
		gap: 40px;
	}

	#textbox {
		display: flex;
		flex-direction: column;
		gap: 10px;
	}

	@media (max-width: 1000px) {
		section {
			padding: 120px 20px;
			gap: 60px;
		}

		#main-container {
			flex-direction: column;
			align-items: center;
			gap: 30px;
		}

		img {
			width: 140px;
		}

		.text-with-label-1 {
			align-items: center;
			text-align: center;
		}

		.text-with-label-2 {
			padding: 0 10px;
		}
	}
</style>
