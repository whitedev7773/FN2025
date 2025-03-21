<script lang="ts">
	import bg_video from '$lib/assets/background_media.mp4';
	import Section1 from '$lib/components/section/Section1.svelte';
	import Section2 from '$lib/components/section/Section2.svelte';
</script>

<!-- FIXED -->
<div>
	<video autoplay muted loop id="bg_video">
		<source src={bg_video} type="video/mp4" />
	</video>
</div>
<!-- SCROLL -->
<Section1 id="home" />
<Section2 id="introducion" />

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
