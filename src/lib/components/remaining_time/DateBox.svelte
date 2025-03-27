<script lang="ts">
	import Text from '$lib/components/Text.svelte';
	import { onMount } from 'svelte';
	import DateBoxHeader from './DateBoxHeader.svelte';

	export let label: string = '';
	export let display_number: number = 0;

	let number_height: number = 114;
	onMount(() => {
		number_height = document.querySelector('.datebox-content-number')?.scrollHeight ?? 114;
	});

	const numberList = Array.from({ length: 60 }, (_, i) => i);
</script>

<div class="datebox">
	<DateBoxHeader text={label} />
	<div
		class="datebox-content"
		style={`transform: translateY(-${display_number * number_height}px)`}
	>
		{#each numberList as number}
			<div class="datebox-content-number">
				<Text
					fontSize="45px"
					fontWeight="700"
					color="black"
					disable_animation={true}
					mobileFontSize="30px">{number}</Text
				>
			</div>
		{/each}
	</div>
</div>

<style>
	div.datebox {
		width: 120px;
		height: 148px;
		background-color: #fff;
		border-radius: 10px;
		overflow: hidden;
	}

	div.datebox-content {
		z-index: 0;
		position: relative;
		overflow: hidden;

		transition: transform 0.25s ease-out;
	}

	div.datebox-content-number {
		z-index: 0;
		width: 100%;
		height: 114px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	@media (max-width: 768px) {
		div.datebox {
			width: 80px;
			height: 110px;
		}

		div.datebox-content-number {
			height: 76px;
		}
	}
</style>
