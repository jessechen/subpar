<script lang="ts">
    let { data, index, year } = $props();
    const width = $derived((data.reliability.get(year) || 0) * 8);
    const initialY = index*50;
</script>

<circle cx=20 cy={initialY+20} r=20 fill={data.color} />
<text x=20 y={initialY+30} text-anchor="middle" fill={data.color == "#FCCC0A" ? "black" : "white"} class="line-label">{data.name}</text>
<rect x=50 y={initialY} {width} height=40 fill={data.color} />
<text x={width+70} y={initialY+30} class="bar-label">{data.reliability.get(year)}%</text>

<style>
    .line-label {
        font-size: 32px;
    }

    .bar-label {
        font-size: 32px;
    }
</style>