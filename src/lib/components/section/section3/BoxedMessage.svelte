<script lang="ts">
	import '$lib/styles/effects.css';
	const text_list = ['세상의 모든 버그가 사라질 때', '모두가 코딩할 수 있는 날'];
	let text_index = 0;
	let textElement: HTMLParagraphElement | null = null;

	function changeText() {
		text_index = (text_index + 1) % text_list.length;
	}

	// 2초마다 변경
	setInterval(changeText, 2000);
</script>

<div class="shadow-for-dark">
	{#each text_list as text, i}
		{#if i === text_index}
			<p bind:this={textElement} class="animated-text">
				{text}
			</p>
		{/if}
	{/each}
</div>

<style>
	.animated-text {
		font-size: 45px;
		font-weight: 700;
		margin: 0;
		animation: fadeSlide 0.5s cubic-bezier(0.49, 0.15, 0.36, 1.37);
	}

	@keyframes fadeSlide {
		from {
			opacity: 0;
			transform: translateY(10px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	div {
		width: 583px;
		height: 125px;
		display: flex;
		justify-content: center;
		align-items: center;
		border: 4px solid white;
		overflow: hidden;
		position: relative;
		transition: width 0.5s cubic-bezier(0.49, 0.15, 0.36, 1.37);
	}

	@media (max-width: 768px) {
		div {
			width: 320px;
			height: 60px;
		}

		p {
			font-size: 26px !important;
		}
	}
</style>
