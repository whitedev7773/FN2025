<script lang="ts">
	import { MenuOpen } from '$lib/stores/MenuOpen';

	export let text = '';
	export let scrollTo = '';
	export let disabled = false;

	// id를 가진 첫번째 오브젝트로 스크롤
	const scrollToElement = () => {
		MenuOpen.set(false);
		// console.log(scrollTo);
		const element = document.getElementById(scrollTo);
		if (!element) return;
		element.scrollIntoView({ behavior: 'smooth' });
	};

	$: scrollTo = `${scrollTo}`;
</script>

{#if !disabled}
	<a href={scrollTo} on:click={scrollToElement}>{text}</a>
{/if}

<style>
	a {
		position: relative;
		text-decoration: none;
		color: inherit;
		font-size: 18px;
		font-weight: 700;

		display: flex;
		align-items: center;
		justify-content: center;
		height: 40px;

		font-size: '19px';
		font-weight: '700';
	}

	a::after {
		z-index: -1;
		position: absolute;
		content: '';
		display: block;
		width: 100%;
		height: 100%;
		border-radius: 20px;
		padding: 0 16px;

		transition: background-color 0.3s;
	}

	a:hover::after {
		background-color: #2ecc71;
	}

	@media (max-width: 1000px) {
		a {
			font-size: 18px;
		}
	}
</style>
