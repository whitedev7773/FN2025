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
	<div id="logo-and-policy">
		<div id="logo">
			<Text fontSize="30px" fontWeight="700" disable_animation={true} mobileFontSize="20px"
				>FN 2025</Text
			>
			<img id="presented_by" src={PresentedBy} alt="Presented By Fun-Sudal" />
		</div>
		<div id="policy-link-list">
			<a href="./policy">개인정보보호정책</a>
			<a href="./rule">행동강령</a>
		</div>
		<div id="contact" style="display: flex; flex-direction: row; align-items: center; gap: 40px;">
			<Text
				fontSize="16px"
				fontWeight="400"
				color="#7f7f7f"
				mobileFontSize="16px"
				disable_animation={true}>funsudalofficial@gmail.com</Text
			>
			<div class="sns-link-list">
				{#each sns_link as [icon, link]}
					<NetworkIcon imageSrc={icon} {link} />
				{/each}
			</div>
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

	#logo-and-policy {
		display: flex;
		flex-direction: row;
		align-items: center;
		gap: 50px;
	}

	#policy-link-list {
		display: flex;
		flex-direction: row;
		gap: 20px;
	}

	#policy-link-list a {
		color: #7f7f7f;
		font-size: 16px;
		font-weight: 400;
		text-decoration: none;
	}

	@media (max-width: 1000px) {
		footer {
			padding: 20px 30px;
			flex-direction: column;
			gap: 40px;
		}

		#logo {
			width: 100%;
			justify-content: space-between;
		}

		img#presented_by {
			height: 26px;
		}

		#contact {
			flex-direction: column-reverse !important;
			gap: 0px;
			padding-bottom: 20px;
		}

		#logo-and-policy {
			flex-direction: column;
			gap: 40px;
		}
	}
</style>
