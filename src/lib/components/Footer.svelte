<script>
	import Text from '$lib/components/Text.svelte';

	import PresentedBy from '$lib/assets/presented_by_gray.svg';
	import NetworkIcon from '$lib/components/footer/NetworkIcon.svelte';

	import InstagramIcon from '$lib/assets/icon/instagram.svg';
	import YoutubeIcon from '$lib/assets/icon/youtube.svg';
	import MailIcon from '$lib/assets/icon/mail.svg';

	const sns_link = [
		[InstagramIcon, 'https://www.instagram.com/fun_sudal'],
		[YoutubeIcon, 'https://www.youtube.com/@fun_sudal'],
		[MailIcon, 'mailto:funsudalofficial@gmail.com']
	];
</script>

<footer>
	<div id="logo">
		<Text fontSize="30px" fontWeight="700">FN 2025</Text>
		<img src={PresentedBy} alt="Presented By Fun-Sudal" />
	</div>
	<div style="display: flex; flex-direction: row; align-items: center; gap: 40px;">
		<Text fontSize="16px" fontWeight="400" color="#7f7f7f">funsudalofficial@gmail.com</Text>
		<div class="sns-link-list">
			{#each sns_link as [icon, link]}
				<NetworkIcon imageSrc={icon} {link} />
			{/each}
		</div>
	</div>
</footer>

<style>
	footer {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;

		padding: 60px 50px;

		background-color: black;
	}

	#logo {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		gap: 30px;
	}

	div.sns-link-list {
		display: flex;
		flex-direction: row;
		gap: 10px;
	}
</style>
