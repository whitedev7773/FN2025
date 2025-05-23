<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';
	import PosterImage1 from '$lib/assets/posters/1.png';
	import PosterImage2 from '$lib/assets/posters/2.png';

	export let id = '';

	let currentIndex = 0;

	const events = [
		{
			title: '학교에서 알려주지 않는 GPT 사용법',
			description: `모두가 GPT를 사용하는 세상에서 어떻게 살아나가야 할까요?
GPT가 말을 듣게 할 수 있는 총알을 여러분들에게 나눠드릴게요.

어떻게 하면 남들과 다르게 ChatGPT를 쓸 수 있을까요?

과제, 레포트, 메일 등등 이제는 Chat GPT를 쓰지 않는 게 더 어려운 시대죠.
그런데 정말 잘 쓰고 있는 걸까요? 한 문장만 바꿔도 답변의 퀄리티가 완전히 달라집니다.

🫢 “제로샷? 프롬프트?” 몰라도 괜찮아요.

그런 여러분을 위해 공부와 업무 효율을 200% 끌어올릴
《학교에서 안 알려주는 ChatGPT 사용법》 세미나를 준비했어요! 😊`,
			poster: PosterImage1
		},
		{
			title: '이럴 줄 알았으면 안 했다',
			description: `"돈이 없는 리더는 팀을 어떻게 운영해야 할까?"

인스타그램과 유튜브 채널 개설 1개월 만에 누적 조회수 4백만회 달성.
IT 문화를 확산하기 위해 직접 세미나를 열고 있는 팀, 함수달.

그 시작은 개발자 밈이였지만,
어느새 팀을 이끄는 일이 되었습니다.

팀을 만들고 리더가 된 사람의 솔직한 기록.
함수달 리더 권선우가 전하는
신생 팀의 브랜딩, 인스타 바이럴 전략,
그리고 리더십의 시행착오와 인사이트를 공유합니다. 

💬 실전 마케팅 전략이 궁금하다면
💬 최근에 팀을 만들었거나 리더가 된 당신이라면
💬 ‘나만 이런 줄 알았던’ 고민을 나누고 싶다면

바로 이 자리가 답이 될 수 있어요.`,
			poster: PosterImage2
		}
	];

	function prev() {
		if (currentIndex > 0) currentIndex--;
	}

	function next() {
		if (currentIndex < events.length - 1) currentIndex++;
	}

	currentIndex = events.length - 1;
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">SESSION</Text>

	<div class="slider-container">
		<button
			class="nav-button left"
			style="cursor:none; transition: opacity 0.3s; opacity: {currentIndex > 0 ? 1 : 0};"
			on:click={prev}>&larr;</button
		>

		<div class="slider-track" style="transform: translateX(-{currentIndex * 100}%);">
			{#each events as event, i}
				<div class="slide" style="filter: grayscale({i != events.length - 1 ? 1 : 0});">
					<img src={event.poster} alt="poster" />
					<div class="text-content">
						<Text fontSize="38px" fontWeight="700" mobileFontSize="20px">{event.title}</Text>
						<Text fontSize="16px" fontWeight="400" color="#A5A5A5" mobileFontSize="13px">
							{@html event.description.replace(/\n/g, '<br />')}
						</Text>
					</div>
				</div>
			{/each}
		</div>

		<button
			class="nav-button right"
			on:click={next}
			style="cursor: none; transition: opacity 0.3s; opacity: {currentIndex < events.length - 1
				? 1
				: 0};">&rarr;</button
		>
	</div>
</section>

<style>
	section {
		width: 100%;
		box-sizing: border-box;
		padding: 300px 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 100px;
		background-color: var(--navy);
		overflow: hidden;
	}

	.slider-container {
		display: flex;
		align-items: center;
		position: relative;
		width: 100%;
		max-width: 1200px;
		overflow: hidden;
	}

	.slider-track {
		display: flex;
		transition: transform 0.5s cubic-bezier(0.47, 0.36, 0.23, 0.96);
		width: 100%;
	}

	.slide {
		min-width: 100%;
		display: flex;
		gap: 50px;
		justify-content: center;
		align-items: center;
		padding: 0 20px;
		box-sizing: border-box;
	}

	.slide img {
		width: 327px;
		border-radius: 10px;
	}

	.text-content {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.nav-button {
		background: none;
		border: none;
		color: white;
		font-size: 40px;
		cursor: pointer;
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		z-index: 10;
	}

	.nav-button.left {
		left: 10px;
	}

	.nav-button.right {
		right: 10px;
	}

	@media (max-width: 1000px) {
		section {
			padding: 100px 0;
		}

		.slide {
			flex-direction: column;
			text-align: center;
			gap: 20px;
		}

		.slide img {
			width: 200px;
		}

		.nav-button {
			top: 25%;
		}
	}
</style>
