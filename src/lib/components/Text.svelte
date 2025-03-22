<script lang="ts">
	export let tag = 'p'; // 기본값은 'p'
	export let className = '';
	export let style = '';

	// margin, padding 등의 속성 prop으로 받아오기
	export let w = 'fit-content';
	export let h = 'fit-content';
	export let m = '0px';
	export let p = '0px';

	export let mTop = '';
	export let mRight = '';
	export let mBottom = '';
	export let mLeft = '';

	export let pTop = '';
	export let pRight = '';
	export let pBottom = '';
	export let pLeft = '';

	// 글자 스타일 관련 prop
	export let fontSize = '13px';
	export let fontWeight = '400';
	export let color = 'inherit';
	export let textAlign = 'left';

	// 스타일 객체 생성
	const computedStyle = `
		width: ${w};
		height: ${h};
		margin: ${mTop || m} ${mRight || m} ${mBottom || m} ${mLeft || m};
		padding: ${pTop || p} ${pRight || p} ${pBottom || p} ${pLeft || p};
		font-size: ${fontSize};
		font-weight: ${fontWeight};
		color: ${color};
		text-align: ${textAlign};
		${style}
	`;
</script>

<svelte:element this={tag} class={className} style={computedStyle}>
	<slot />
</svelte:element>
