<script lang="ts">
	import { onMount } from 'svelte';

	export let width = 1;
    export let bgColor = 'transparent';
	export let disableMaxWidth = false;
	export let customBindingClass = 'resizable';

	let resizeHandler: HTMLElement;
	let resizing: boolean = false;
	let startX: number, endX: number;
	let startWidth: number;
	let parent: HTMLElement;
	let windowWidth: number;

	onMount(() => {
		parent = resizeHandler.closest('.' + customBindingClass) as HTMLElement;
		parent.style.position = 'relative';
		if (!disableMaxWidth) parent.style.maxWidth = '100%';
		window?.addEventListener('mousemove', (e) => {
			if (!resizing || !parent) return;
			endX = e.pageX;
			parent.style.width = startWidth + (endX - startX) + 'px';
		});
		window?.addEventListener('mouseup', (e) => {
			resizing = false;
		});
	});
</script>

<svelte:window bind:innerWidth={windowWidth} />

<div
	bind:this={resizeHandler}
	id="resize-handler"
	style="width: {width}px; background-color: {bgColor};"
	on:mousedown={(e) => {
		startX = e.pageX;
		startWidth = parent.offsetWidth;
		resizing = true;
	}}
/>

<style>
	#resize-handler {
		position: absolute;
		right: 0;
		top: 0;
		bottom: 0;
		cursor: col-resize;
		opacity: 0;
	}
</style>
