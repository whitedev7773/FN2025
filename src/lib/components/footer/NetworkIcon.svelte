<script lang="ts">
	export let link = '';
	export let imageSrc = '';
</script>

<a href={link} target="_blank">
	<img src={imageSrc} alt={link} width="26px" height="26px" style="opacity: 0.5" />
</a>

<style>
	a {
		width: 60px;
		height: 60px;

		display: flex;
		justify-content: center;
		align-items: center;

		text-decoration: none;
		background-color: #1c1c1c;

		border-radius: 50%;
	}
</style>
