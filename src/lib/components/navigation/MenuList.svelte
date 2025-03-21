<script lang="ts">
	import { onMount } from 'svelte';

	import MenuButton from '$lib/components/navigation/MenuButton.svelte';
	import type { MenuButtonType } from '$lib/utils/MenuButtonType';

	// 첫접속 시 #에 붙은 주소 확인 후 그 곳으로 미리 scroll
	onMount(() => {
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
		{ text: 'LOCATION', scroll_to: '#location' },
		{ text: 'FAQ', scroll_to: '#faq' }
	];
</script>

<div>
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
</style>
