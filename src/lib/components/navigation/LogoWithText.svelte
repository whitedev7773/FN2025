<script lang="ts">
	import Logo from '$lib/assets/logo.svg';
	import Text from '$lib/components/Text.svelte';

	export let text = '';

	const logo_size = '48px';
</script>

<div>
	<img width={logo_size} height={logo_size} src={Logo} alt="{text}의 로고" />
	<Text fontSize="25px" fontWeight="700" disable_animation={true}>{text}</Text>
</div>

<style>
	div {
		display: flex;
		align-items: center;
		gap: 8px;
	}
</style>
