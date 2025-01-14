<script lang="ts">
    import Bar from './Bar.svelte';

    const initialYear: number = 2015;
    const lines: Array<Line> = [];
    let year: number = $state(2024);

    class Line {
        public name: string;
        public color: string;
        public reliability: Map<number, number>;

        public constructor(name: string, color: string, performance: Array<number>) {
            if (performance.length != 10) {
                throw `${name} has array of ${performance.length} years, expected 10`
            }
            this.name = name;
            this.color = color;
            this.reliability = new Map();
            performance.forEach((perf, index) => {
                this.reliability.set(index + initialYear, perf);
            });
        }
    }

    lines.push(new Line("1", "red", 
        [76.26, 71.44, 69.39, 72.23, 86.69, 91.94, 87.44, 82.25, 82.26, 79.81]));
    lines.push(new Line("2", "red", 
        [42.87, 36.18, 30.31, 51.79, 71.63, 84.62, 81.73, 74.75, 76.00, 72.84]));
    lines.push(new Line("3", "red", 
        [65.19, 57.76, 49.59, 67.54, 82.62, 89.94, 87.10, 84.75, 86.37, 84.77]));
    lines.push(new Line("4", "green", 
        [43.22, 37.67, 32.73, 53.87, 73.55, 87.77, 84.14, 81.02, 83.18, 81.80]));
    lines.push(new Line("5", "green", 
        [39.79, 37.15, 31.54, 59.00, 80.30, 87.28, 85.54, 81.05, 82.49, 80.82]));
    lines.push(new Line("6", "green", 
        [46.07, 48.40, 51.70, 59.73, 78.61, 88.65, 86.46, 79.30, 79.66, 77.02]));
    lines.push(new Line("7", "purple", 
        [82.91, 77.50, 72.52, 67.77, 90.49, 93.50, 90.57, 90.59, 91.04, 91.14]));
    lines.push(new Line("A", "blue", 
        [66.36,	62.43, 54.93, 52.31, 68.90, 81.63, 73.01, 69.06, 72.08, 76.21]));
    lines.push(new Line("F", "orange", 
        [57.34, 58.16, 45.70, 45.22, 66.11, 82.11, 74.20, 71.34, 70.15, 69.59]));
</script>

<main>
    <header>
        <h1>NYC Subway on-time performance for {year}</h1>
        <input class="slider" type="range" id="year" min={initialYear} max="2024" bind:value={year}/>
    </header>
    <svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
        {#each lines as line, index}
            <Bar data={line} {index} {year} />
        {/each}
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

    h1 {
        font-size: 28px;
    }

	.slider {
		width: 100%;
	}
</style>
