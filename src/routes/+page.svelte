<script lang="ts">
    import Row from './Row.svelte';

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

    lines.push(new Line("1", "#EE352E",
        [76.26, 71.44, 69.39, 72.23, 86.69, 91.94, 87.44, 82.25, 82.26, 79.81]));
    lines.push(new Line("2", "#EE352E",
        [42.87, 36.18, 30.31, 51.79, 71.63, 84.62, 81.73, 74.75, 76.00, 72.84]));
    lines.push(new Line("3", "#EE352E",
        [65.19, 57.76, 49.59, 67.54, 82.62, 89.94, 87.10, 84.75, 86.37, 84.77]));
    lines.push(new Line("4", "#00933C",
        [43.22, 37.67, 32.73, 53.87, 73.55, 87.77, 84.14, 81.02, 83.18, 81.80]));
    lines.push(new Line("5", "#00933C",
        [39.79, 37.15, 31.54, 59.00, 80.30, 87.28, 85.54, 81.05, 82.49, 80.82]));
    lines.push(new Line("6", "#00933C",
        [46.07, 48.40, 51.70, 59.73, 78.61, 88.65, 86.46, 79.30, 79.66, 77.02]));
    lines.push(new Line("7", "#B933AD",
        [82.91, 77.50, 72.52, 67.77, 90.49, 93.50, 90.57, 90.59, 91.04, 91.14]));
    lines.push(new Line("A", "#0039A6",
        [66.36,	62.43, 54.93, 52.31, 68.90, 81.63, 73.01, 69.06, 72.08, 76.21]));
    lines.push(new Line("C", "#0039A6",
        [78.82, 69.23, 58.94, 56.18, 74.22, 87.38, 77.37, 68.82, 72.63, 71.26]));
    lines.push(new Line("E", "#0039A6",
        [69.05, 67.23, 59.10, 56.60, 79.29, 87.15, 77.62, 71.75, 74.29, 76.62]));
    lines.push(new Line("B", "#FF6319",
        [76.47, 67.40, 53.94, 54.90, 65.50, 81.12, 75.56, 68.27, 75.90, 64.63]));
    lines.push(new Line("D", "#FF6319",
        [73.89, 66.46, 54.09, 54.45, 68.84, 82.34, 75.46, 72.62, 73.37, 71.45]));
    lines.push(new Line("F", "#FF6319",
        [57.34, 58.16, 45.70, 45.22, 66.11, 82.11, 74.20, 71.34, 70.15, 69.59]));
    lines.push(new Line("M", "#FF6319",
        [69.49, 67.18, 70.34, 68.43, 77.21, 90.74, 83.45, 79.38, 85.90, 83.34]));
    lines.push(new Line("G", "#6CBE45",
        [67.55, 80.21, 73.62, 68.03, 79.06, 87.64, 85.43, 88.50, 86.26, 86.06]));
    lines.push(new Line("J/Z", "#996633",
        [72.65, 64.70, 65.76, 61.52, 79.54, 90.62, 90.50, 84.84, 88.12, 81.66]));
    lines.push(new Line("L", "#A7A9AC",
        [91.80, 90.35, 93.59, 90.58, 92.40, 94.00, 92.68, 91.12, 92.36, 91.45]));
    lines.push(new Line("N/W", "#FCCC0A",
        [66.14, 61.71, 55.16, 57.62, 74.35, 76.97, 78.34, 76.33, 73.62, 75.21]));
    lines.push(new Line("Q", "#FCCC0A",
        [70.59, 69.95, 65.60, 67.10, 84.00, 87.37, 77.50, 74.46, 78.35, 78.01]));
    lines.push(new Line("R", "#FCCC0A",
        [59.08, 59.48, 67.81, 54.27, 73.02, 86.32, 82.03, 77.42, 79.62, 77.26]));
</script>

<svelte:head>
    <title>NYC Subway on-time performance</title>
    <meta name="description" content="An interactive chart of weekday on-time performance for each MTA subway line from 2015 to 2024" />
</svelte:head>
<main>
    <header>
        <h1>{year} NYC Subway <abbr title="A train is defined as being on-time if it arrives at its destination terminal on-time, early, or no more than five minutes late, and that has not skipped any planned station stops.">on-time</abbr> performance</h1>
        <input class="slider" type="range" id="year" min={initialYear} max="2024" bind:value={year} list="years"/>
        <datalist id="years">
            <option value="2015"></option>
            <option value="2016"></option>
            <option value="2017"></option>
            <option value="2018"></option>
            <option value="2019"></option>
            <option value="2020"></option>
            <option value="2021"></option>
            <option value="2022"></option>
            <option value="2023"></option>
            <option value="2024"></option>
        </datalist>
        <aside class="legend">
            <p class="left-legend">← less reliable</p>
            <p class="right-legend">more reliable →</p>
        </aside>
    </header>
    <svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
        {#each lines as line, index}
            <Row data={line} {index} {year} />
        {/each}
    </svg>
</main>
<div class="controls">
    <!-- Sort-descending icon created by yaicon - Flaticon -->
     <button type="button">
        <img src="/sort.png" height="32" width="32" alt="Sort by value"/>
     </button>
</div>

<style>
    main {
        width: calc(100vmin - 100px);
        height: calc(100vmin - 100px);
    }

    svg {
        width: 100%;
        height: 100%;
    }

    h1 {
        font-size: 24px;
        margin: 0;
    }

    .slider {
        width: 100%;
        cursor: grab;
        margin-bottom: 12px;
    }

    .slider:active {
        cursor: grabbing;
    }

    .legend {
        display: flex;
        justify-content: space-between;
        font-size: 14px;
    }

    .left-legend {
        margin-left: calc(10vmin - 10px);
    }

    .right-legend {
        margin-right: calc(10vmin - 10px);
    }

    p {
        margin: 0 0 4px 0;
    }

    .controls {
        position: absolute;
        right: 12px;
        bottom: 12px;
    }

    button {
        cursor: pointer;
        padding: 2px;
    }

    img {
        display: block;
    }
</style>
