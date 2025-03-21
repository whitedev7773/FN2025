<script lang="ts">
	import { onMount } from 'svelte';

	const size = 16;

	// 따라다니는 커서
	// <button> 또는 <a>에 닿으면 사이즈가 2배 커지게
	// 단, 터치 디바이스일 땐 opacity 0으로 숨김
	onMount(() => {
		const cursor = document.querySelector('span');
		const links = document.querySelectorAll('a, button');

		cursor && window.addEventListener('touchstart', () => (cursor.style.opacity = '0'));

		cursor &&
			links.forEach((link) => {
				link.addEventListener('mouseover', () => {
					cursor.style.width = `${size * 1.8}px`;
					cursor.style.height = `${size * 1.8}px`;
				});

				link.addEventListener('mouseleave', () => {
					cursor.style.width = `${size}px`;
					cursor.style.height = `${size}px`;
				});
			});

		cursor &&
			document.addEventListener('mousemove', (e) => {
				cursor.style.top = e.pageY + 'px';
				cursor.style.left = e.pageX + 'px';
			});
	});
</script>

<span></span>

<style>
	span {
		position: fixed;
		top: 0;
		left: 0;
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background-color: #fff;
		mix-blend-mode: difference;
		pointer-events: none;
		z-index: 9999;
		transform: translate(-50%, -50%);
		transition:
			width 0.3s,
			height 0.3s;
	}
</style>
