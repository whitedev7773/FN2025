<script lang="ts">
	export let isTitle = false;

	// margin, padding 등의 속성 prop으로 받아오기
	export let m = '0px';
	export let p = '0px';

	export let mTop = '0px';
	export let mRight = '0px';
	export let mBottom = '0px';
	export let mLeft = '0px';

	export let pTop = '0px';
	export let pRight = '0px';
	export let pBottom = '0px';
	export let pLeft = '0px';

	// 글자 크기, 색상 등의 속성 prop으로 받아오기
	export let fontSize = '13px';
	export let fontWeight = '400';
	export let color = 'inherit';

	// 글자 정렬 속성 prop으로 받아오기
	export let textAlign = 'left';

	// 그 외 속성 prop으로 받아오기
	export let className = '';
	export let style = '';
</script>

{#if isTitle}
	<h1
		class={className}
		style="margin: {m}; padding: {p}; margin-top: {mTop}; margin-right: {mRight}; margin-bottom: {mBottom}; margin-left: {mLeft}; padding-top: {pTop}; padding-right: {pRight}; padding-bottom: {pBottom}; padding-left: {pLeft}; font-size: {fontSize}; font-weight: {fontWeight}; color: {color}; text-align: {textAlign}; {style}"
	>
		<slot />
	</h1>
{:else}
	<p
		class={className}
		style="margin: {m}; padding: {p}; margin-top: {mTop}; margin-right: {mRight}; margin-bottom: {mBottom}; margin-left: {mLeft}; padding-top: {pTop}; padding-right: {pRight}; padding-bottom: {pBottom}; padding-left: {pLeft}; font-size: {fontSize}; font-weight: {fontWeight}; color: {color}; text-align: {textAlign}; {style}"
	>
		<slot />
	</p>
{/if}
