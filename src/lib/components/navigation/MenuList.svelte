<script lang="ts">
	import { onMount } from 'svelte';

	import MenuButton from '$lib/components/navigation/MenuButton.svelte';
	import type { MenuButtonType } from '$lib/utils/MenuButtonType';
	import { MenuOpen } from '$lib/stores/MenuOpen';

	$: isTouch = false;

	// 첫접속 시 #에 붙은 주소 확인 후 그 곳으로 미리 scroll
	onMount(() => {
		window.addEventListener('touchstart', () => (isTouch = true));
		const hash = window.location.hash;
		if (hash) {
			const target = document.querySelector(hash);
			if (target) {
				target.scrollIntoView({ behavior: 'smooth' });
			}
		}
	});

	export let items: MenuButtonType[] = [
		{ text: 'INTRODUCTION', scroll_to: '#introducion' },
		{ text: 'SESSION', scroll_to: '#sessions' },
		{ text: 'SPONSERS', scroll_to: '#sponsers' },
		{ text: 'LOCATION', scroll_to: '#location' }
		// { text: 'FAQ', scroll_to: '#faq' }
	];

	let div: HTMLDivElement | null = null;
	$: MenuOpen;

	// 햄버거 버튼 클릭 시 메뉴 보이기
	function openMenu() {
		if (!div) {
			return;
		}

		MenuOpen.set(!$MenuOpen);
	}
</script>

<button on:click={openMenu} class="hamburger"> ☰ </button>

<div
	bind:this={div}
	style="opacity: {$MenuOpen ? 1 : 0}; pointer-events: {!isTouch
		? 'auto'
		: $MenuOpen
			? 'auto'
			: 'none'}"
>
	{#each items as item}
		<MenuButton text={item.text} scrollTo={item.scroll_to} disabled={item.disabled} />
	{/each}
</div>

<style>
	div {
		display: flex;
		align-items: center;
		gap: 60px;
	}

	button.hamburger {
		display: none;
		color: white;
		z-index: 10000;
		background-color: transparent;
		border: none;
		outline: none;
	}

	/* pc 반응형 */
	@media (min-width: 769px) {
		div {
			opacity: 1 !important;
		}
	}

	@media (max-width: 768px) {
		button.hamburger {
			display: block;
			font-size: 30px;
		}

		div {
			position: fixed;
			top: 0;
			left: 0;
			width: 100%;
			height: 100vh;
			padding-top: 60px;
			background-color: #000000dd;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			gap: 40px;
			opacity: 0;
			pointer-events: none;
			transition: opacity 0.3s;
		}
	}
</style>
