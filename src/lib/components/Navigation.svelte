<script lang="ts">
	import LogoWithText from '$lib/components/navigation/LogoWithText.svelte';
	import MenuList from './navigation/MenuList.svelte';

	import { sectionScrollY } from '$lib/stores/SectionScrollY';

	// $: console.log($sectionScrollY);
	$: isGlass = $sectionScrollY > 300 ? 'glass' : '';
</script>

<div class={isGlass}>
	<LogoWithText text="FN 2025" />
	<MenuList />
</div>

<style>
	div {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		background-color: transparent;
		z-index: 9000;

		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0px 60px;
		height: 90px;
		box-sizing: border-box;

		user-select: none;

		transition:
			background-color 0.3s,
			filter 0.3s;
	}

	.glass {
		background-color: #ffffff20 !important;
		backdrop-filter: blur(10px);
	}

	@media (max-width: 768px) {
		div {
			height: 70px;
			padding: 0px 20px;
		}
	}
</style>
