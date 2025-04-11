<script lang="ts">
	import Logo from '$lib/assets/logo.svg';

	export let text = '';

	const logo_size = '42px';
</script>

<div>
	<img width={logo_size} height={logo_size} src={Logo} alt="{text}의 로고" />
	<p>{text}</p>
</div>

<style>
	div {
		display: flex;
		align-items: center;
		gap: 8px;
	}

	p {
		font-size: 22px;
		font-weight: 700;
	}

	@media (max-width: 1000px) {
		img {
			width: 36px;
			height: 36px;
		}

		p {
			font-size: 18px !important;
		}
	}
</style>
