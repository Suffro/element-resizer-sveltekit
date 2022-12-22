<script lang="ts">
	import ResizeHandler from '$lib/components/resizeHandler.svelte';
	import '../app.css';
</script>

<div id="example">
	<h1>Resizable handler example:</h1>
	<!--
    Is important that you give the "resizable" class to the parent,
    NOTE: you can set a custom class using "customBindingClass" prop of resizeHandler.svelte.
    -->
	<div id="resizable-container" class="resizable">
		Resizable element
		<ResizeHandler width={3} bgColor="red"/>
	</div>
	<!-- / -->

	<p>
		Made with &#10084;&#65039; by <a href="https://github.com/Suffro">Lorenzo</a>
	</p>
</div>

<style>
	#example {
		display: grid;
		justify-content: center;
		width: 100%;
		height: 100%;
	}
	#resizable-container {
		padding: 10px;
		border-radius: 10px;
		background-color: rgba(0, 0, 0, 0.2);
		width: fit-content;
	}
</style>
