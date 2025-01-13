<script lang="ts">
    import Line from './Line.svelte';
</script>

<header>
    <input class="slider" type="range" id="year" min="2015" max="2024" />
</header>
<main>
    <svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
    </svg>
</main>

<style>
	header {
		height: 50px;
		width: calc(100vmin - 50px);
		display: flex;
		align-items: center;
		justify-content: center;
	}

	main {
		width: calc(100vmin - 50px);
		height: calc(100vmin - 50px);
	}

	svg {
		width: 100%;
		height: 100%;
        background-color: red;
	}

	.slider {
		width: 100%;
	}
</style>
