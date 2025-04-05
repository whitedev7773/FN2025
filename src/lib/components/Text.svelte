<script lang="ts">
	import { onMount } from 'svelte';

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

	// 모바일용 폰트 사이즈
	export let mobileFontSize: string | null = null;

	// 스타일 객체 생성
	let computedStyle = '';
	let isVisible = false;
	let element: HTMLElement;

	export let disable_animation = false;

	const updateStyle = () => {
		const isMobile = window.matchMedia('(max-width: 1000px)').matches;
		const appliedFontSize = isMobile ? (mobileFontSize ?? fontSize) : fontSize;

		computedStyle = `
			width: ${w};
			height: ${h};
			margin: ${mTop || m} ${mRight || m} ${mBottom || m} ${mLeft || m};
			padding: ${pTop || p} ${pRight || p} ${pBottom || p} ${pLeft || p};
			font-size: ${appliedFontSize};
			font-weight: ${fontWeight};
			color: ${color};
			text-align: ${textAlign};
			${style}
		`;
	};

	onMount(() => {
		updateStyle();

		// 반응형 업데이트를 위해 resize 이벤트 추가
		const resizeListener = () => updateStyle();
		window.addEventListener('resize', resizeListener);

		if (disable_animation) {
			isVisible = true;
			return;
		}

		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					isVisible = entry.isIntersecting;
				});
			},
			{ threshold: 1 } // 100% 보이면 트리거
		);

		if (element) observer.observe(element);

		return () => {
			window.removeEventListener('resize', resizeListener);
			if (element) observer.unobserve(element);
		};
	});
</script>

<svelte:element
	this={tag}
	bind:this={element}
	class={className}
	style={`${computedStyle}; opacity: ${isVisible ? 1 : 0}; transition: opacity 0.6s 0.3s;`}
>
	<slot />
</svelte:element>
