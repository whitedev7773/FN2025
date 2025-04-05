<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';
	import RemainingTime from '$lib/components/RemainingTime.svelte';

	import peeeup from '$lib/assets/v.svg'; // ㅍ
	import au from '$lib/assets/j.svg'; // ㅓ
	import iieung from '$lib/assets/d.svg'; // ㅇ

	export let id = '';
</script>

<section {id}>
	<!-- FIXED -->
	<img class="peeeup" src={peeeup} width="432px" height="356px" alt="ㅍ 꾸밈요소" />
	<img class="au" src={au} width="216" height="601" alt="ㅓ 꾸밈요소" />
	<img class="iieung-bottom" src={iieung} width="639px" height="535px" alt="ㅇ 하단 꾸밈요소" />
	<img class="iieung-top" src={iieung} width="676px" height="567px" alt="ㅇ 상단 꾸밈요소" />
	<!-- SCROLL -->
	<Text
		fontSize="27px"
		fontWeight="700"
		textAlign="center"
		color="#ffffff77"
		mBottom="50px"
		mobileFontSize="20px">Introduction</Text
	>
	<Text fontSize="54px" fontWeight="700" textAlign="center" mBottom="50px" mobileFontSize="34px"
		>FN은 이런 세미나에요</Text
	>
	<Text fontSize="25px" fontWeight="400" textAlign="center" mBottom="150px" mobileFontSize="16px"
		>주니어 개발자와 함께 성장하기 위한 하나의 발판으로써,<br />
		현장에서 도움이 되는 Tips를 소개해드려요.</Text
	>
	<Text fontSize="30px" fontWeight="500" textAlign="center" mBottom="20px" mobileFontSize="20px"
		>펑의 시작까지 이만큼 남았어요</Text
	>
	<RemainingTime />
</section>

<style>
	section {
		position: relative;
		padding: 250px 0;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
		background-color: var(--light-navy);

		overflow: hidden;
	}

	img {
		filter: invert(0.5);
		position: absolute;
		user-select: none;

		transition:
			top 0.4s ease-in-out,
			left 0.4s ease-in-out,
			bottom 0.4s ease-in-out,
			right 0.4s ease-in-out,
			filter 0.2s ease-out;
	}

	img:hover {
		filter: invert(0);
	}

	.peeeup {
		top: 84px;
		left: 101px;
	}

	.au {
		bottom: 106px;
		right: 358px;
	}

	.iieung-bottom {
		bottom: -157px;
		left: -123px;
	}

	.iieung-top {
		top: -101px;
		right: -391px;
	}

	@media (max-width: 1000px) {
		.peeeup {
			top: 0px;
			left: -10px;
		}

		.au {
			bottom: -50px;
			right: 0px;
		}

		.iieung-bottom {
			bottom: -200px;
			left: -303px;
		}

		.iieung-top {
			top: -101px;
			right: -391px;
		}
	}

	@media (max-width: 768px) {
		img {
			opacity: 0;
		}
	}
</style>
