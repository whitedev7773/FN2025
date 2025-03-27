<script lang="ts">
	import '$lib/styles/color.css';

	import Logo from '$lib/assets/logo.svg';
	import PresentedBy from '$lib/assets/presented_by_white.svg';

	import { onMount } from 'svelte';

	let logo_x = -50;
	let logo_y = -100;
	let text_x = -123;
	let text_y = -50;

	let logo_opacity = 0;
	let text_opacity = 0;

	let circle_scale = 0;

	let whole_opacity = 1;

	onMount(() => {
		setTimeout(() => {
			logo_y = -50;
			logo_opacity = 1;
			setTimeout(() => {
				logo_x = 35;
				text_x = -85;
				text_opacity = 1;
				setTimeout(() => {
					circle_scale = 1;
					setTimeout(() => {
						whole_opacity = 0;
					}, 1000);
				}, 1000);
			}, 500);
		}, 500);
	});
</script>

<div id="intro-bg" style="opacity: {whole_opacity};">
	<img
		id="logo"
		style="transform: translate({logo_x}%, {logo_y}%); opacity: {logo_opacity}"
		src={Logo}
		alt="intro-logo"
		width="100px"
		height="100px"
	/>
	<img
		id="text"
		style="transform: translate({text_x}%, {text_y}%); opacity: {text_opacity}"
		src={PresentedBy}
		alt="intro-text"
		width="166px"
		height="28px"
	/>
	<div
		id="circle"
		style="transform: translate(-50%, -50%) scale({circle_scale}, {circle_scale});"
	></div>
</div>

<style>
	#intro-bg {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100vh;
		z-index: 10000;

		user-select: none;
		pointer-events: none;

		background-color: var(--dark-green);
		transition: opacity 1.5s ease-in-out;
	}

	img#logo {
		position: absolute;
		top: 50%;
		left: 50%;
		opacity: 1;
		/* transform: translate(3%, -50%); */
		transition:
			transform 0.45s,
			opacity 0.45s;
	}

	#text {
		position: absolute;
		top: 50%;
		left: 50%;
		opacity: 1;
		/* transform: translate(-103%, -50%); */
		transition:
			transform 0.45s,
			opacity 0.45s;
	}

	#circle {
		position: absolute;
		top: 50%;
		left: 50%;
		width: 200vh;
		height: 200vh;
		border-radius: 50%;
		background-color: white;

		transition: transform 1.5s cubic-bezier(0.71, 0.09, 0.24, 0.93);
	}
</style>
