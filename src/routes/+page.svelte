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
            this.name = name;
            this.color = color;
            this.reliability = new Map();
            performance.forEach((perf, index) => {
                this.reliability.set(index + initialYear, perf);
            });
        }
    }

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
        <Bar data={lines[0]} index={0} {year} />
        <Bar data={lines[1]} index={1} {year} />
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
