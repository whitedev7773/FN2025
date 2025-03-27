<script lang="ts">
	import bg_video from '$lib/assets/background_media.mp4';
	import Footer from '$lib/components/Footer.svelte';
	import Section1 from '$lib/components/section/Section1.svelte';
	import Section2 from '$lib/components/section/Section2.svelte';
	import Section3 from '$lib/components/section/Section3.svelte';
	import Section4 from '$lib/components/section/Section4.svelte';
	import Section5 from '$lib/components/section/Section5.svelte';
	import Section6 from '$lib/components/section/Section6.svelte';
	import Section9 from '$lib/components/section/Section9.svelte';
</script>

<svelte:head>
	<title>FN 2025</title>
	<meta name="description" content="함수달이 준비한 첫번째 세미나, FN 2025" />
</svelte:head>

<!-- FIXED -->
<div>
	<video autoplay muted loop id="bg_video">
		<source src={bg_video} type="video/mp4" />
	</video>
</div>
<!-- SCROLL -->
<Section1 id="home" />
<Section2 id="introducion" />
<!-- <Section3 id="fn2025" /> -->
<!-- <Section4 id="sessions" /> -->
<!-- <Section5 id="sponsers" /> -->
<!-- <Section6 id="location" /> -->
<!-- <Section9 id="fn2025" /> -->
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
