<script lang="ts">
	import '$lib/styles/color.css';
	import Text from '$lib/components/Text.svelte';

	import MapImage from '$lib/assets/map.png';

	export let id = '';
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">LOCATION</Text>
	<div id="main-container">
		<img src={MapImage} alt="map" height="340px" />
		<div id="textbox" class="text-with-label-1">
			<Text fontSize="34px" fontWeight="600" mobileFontSize="20px">경북대학교 대구캠퍼스</Text>
			<Text fontSize="19px" fontWeight="500" color="#A5A5A5" mobileFontSize="14px"
				>IT대학 4호관 지하1층 DIY실</Text
			>
		</div>
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
		gap: 70px;

		background-color: var(--navy);
	}

	#main-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		gap: 50px;
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
		gap: 30px;
	}

	@media (max-width: 1000px) {
		section {
			padding: 100px 0;
		}

		#main-container {
			flex-direction: column;
			gap: 30px;
		}

		#textbox {
			width: calc(90% - 32px);
			gap: 10px;
		}

		img {
			width: 90%;
			max-width: 500px;
			height: auto;
		}
	}
</style>
