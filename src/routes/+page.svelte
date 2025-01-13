<script lang="ts">
    import Line from './Line.svelte';

    let year: number = 2024;
</script>

<main>
    <header>
        <h1>OTP for {year}</h1>
        <input class="slider" type="range" id="year" min="2015" max="2024" bind:value={year}/>
    </header>
    <svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
        <Line name="A" color="blue" x={0} y={0} width={202} height={80} />
        <Line name="F" color="orange" x={0} y={100} width={302} height={80} />
    </svg>
</main>

<style>
	main {
		width: calc(100vmin - 50px);
		height: calc(100vmin - 50px);
	}

	svg {
		width: 100%;
		height: 100%;
	}

	.slider {
		width: 100%;
	}
</style>
