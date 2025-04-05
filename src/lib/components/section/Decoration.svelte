<script lang="ts">
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';
	import RemainingTime from '../RemainingTime.svelte';

	import peeeup from '$lib/assets/v.svg'; // ㅍ
	import au from '$lib/assets/j.svg'; // ㅓ
	import iieung from '$lib/assets/d.svg'; // ㅇ

	export let id = '';
</script>

<section {id}>
	<!-- FIXED -->
	<img class="peeeup" src={peeeup} width="432px" height="356px" alt="ㅍ 꾸밈요소" />
	<img class="au" src={au} width="216" height="601" alt="ㅓ 꾸밈요소" />
	<img class="iieung" src={iieung} width="639px" height="535px" alt="ㅇ 꾸밈요소" />
</section>

<style>
	section {
		position: relative;
		height: 246px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
		background-color: var(--light-navy);

		overflow: hidden;
	}

	img {
		position: absolute;
		user-select: none;
	}

	.peeeup {
		top: 50%;
		left: -8px;
		transform: translateY(-50%);
	}

	.au {
		top: 60%;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	.iieung {
		top: 50%;
		right: -213px;
		transform: translateY(-50%);
	}

	@media (max-width: 1000px) {
		section {
			height: 100px;
		}

		.peeeup {
			width: auto;
			height: 130px;
			left: -50px;
		}

		.au {
			width: auto;
			height: 180px;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
		}

		.iieung {
			width: auto;
			height: 160px;
			right: -90px;
		}
	}
</style>
