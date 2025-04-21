<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';

	import funSudal from '$lib/assets/sponser/funsudal.png';

	export let id = '';

	const logo_list = [funSudal];
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">SPONSERS</Text>
	<div id="main-container">
		{#each logo_list as logo}
			<div id="sponser-logo">
				<img src={logo} alt={logo} width="100%" />
			</div>
		{/each}
	</div>
</section>

<style>
	section {
		width: 100%;
		box-sizing: border-box;
		padding: 100px 0;

		position: relative;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 70px;

		background-color: var(--navy);
	}

	#main-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		opacity: 0.5;
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

	#sponser-logo {
		width: 280px;
	}

	@media (max-width: 1000px) {
		#main-container {
			flex-direction: column;
			gap: 0px;
		}

		#sponser-logo {
			width: 200px;
		}
	}
</style>
