<script lang="ts">
	import { onMount } from 'svelte';

	import '$lib/styles/global.css';

	import Cursor from '$lib/components/Cursor.svelte';
	import Navigation from '$lib/components/Navigation.svelte';
	import { sectionScrollY } from '$lib/stores/SectionScrollY';

	import bg_video from '$lib/assets/background_media.mp4';
	import Footer from '$lib/components/Footer.svelte';
	import Intro from '$lib/components/Intro.svelte';

	import MainSection from '$lib/components/section/MainSection.svelte';
	import Introduction from '$lib/components/section/Introduction.svelte';
	import Brand from '$lib/components/section/Brand.svelte';
	import Session from '$lib/components/section/Session.svelte';
	import Lecturer from '$lib/components/section/Lecturer.svelte';
	import Sponser from '$lib/components/section/Sponser.svelte';
	import Location from '$lib/components/section/Location.svelte';
	import Decoration from '$lib/components/section/Decoration.svelte';

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

<svelte:head>
	<title>FN 2025</title>
	<meta name="description" content="함수달이 준비한 첫번째 세미나, FN 2025" />
</svelte:head>

<Intro />
<Cursor />
<Navigation />
<!-- FIXED -->
<div>
	<video autoplay muted loop id="bg_video">
		<source src={bg_video} type="video/mp4" />
	</video>
</div>
<!-- SCROLL -->
<MainSection id="home" />
<Introduction id="introducion" />
<Brand id="fn2025" />
<Session id="sessions" />
<Lecturer id="lecturer" />
<Sponser id="sponsers" />
<Location id="location" />
<Decoration id="fn2025" />
<Footer />

<style>
	div {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100vh;
		z-index: -100;
	}

	video {
		object-fit: cover;
		width: 100%;
		height: 100%;
		filter: brightness(0.7) blur(8px);
	}
</style>
