<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';

	import funSudal from '$lib/assets/sponser/funsudal.png';
	import kert from '$lib/assets/sponser/kert.png';
	import swKnuEdu from '$lib/assets/sponser/sw_knu_edu.png';

	export let id = '';

	const logo_list = [funSudal, kert, swKnuEdu];
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700">SPONSERS</Text>
	<div id="main-container">
		{#each logo_list as logo}
			<div style="width: 280px">
				<img src={logo} alt={logo} />
			</div>
		{/each}
	</div>
</section>

<style>
	section {
		width: 100%;
		box-sizing: border-box;
		padding: 300px 0;

		position: relative;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 100px;

		background-color: var(--navy);
	}

	#main-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		opacity: 0.5;
	}

	img {
		border-radius: 10px;
	}

	#container {
		display: flex;
		flex-direction: column;
		gap: 40px;
	}

	#textbox {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		gap: 10px;
	}
</style>
