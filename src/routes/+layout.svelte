<script lang="ts">
	import { onMount } from 'svelte';

	import '$lib/styles/global.css';

	import Cursor from '$lib/components/Cursor.svelte';
	import Navigation from '$lib/components/Navigation.svelte';
	import { sectionScrollY } from '$lib/stores/SectionScrollY';

	// sectionScrollY에 div의 스크롤값 저장

	onMount(() => {
		const div = document.querySelector('#section_page');
		if (div) {
			div.addEventListener('scroll', () => {
				sectionScrollY.set(div.scrollTop);
			});
		}
	});
</script>

<Cursor />
<Navigation />
<div id="section_page">
	<slot />
</div>

<style>
	div {
		scroll-behavior: smooth;
		height: 100vh;
		overflow-y: scroll;
	}
</style>
