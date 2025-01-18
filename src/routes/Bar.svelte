<script lang="ts">
    let { data, index, year } = $props();
    const width: number = $derived((data.reliability.get(year) || 0) * 8);
    const initialY: number = index*50;

    const rightName: string = data.name.includes('/') ? data.name.split('/')[1] : data.name
    const leftName: string = data.name.includes('/') ? data.name.split('/')[0] : ""
</script>

{#if leftName}
    <circle cx=20 cy={initialY+20} r=20 fill={data.color} />
    <text x=20 y={initialY+30} text-anchor="middle" fill={data.color == "#FCCC0A" ? "black" : "white"} class="line-label">{leftName}</text>
{/if}
<circle cx=70 cy={initialY+20} r=20 fill={data.color} />
<text x=70 y={initialY+30} text-anchor="middle" fill={data.color == "#FCCC0A" ? "black" : "white"} class="line-label">{rightName}</text>
<rect x=100 y={initialY} {width} height=40 fill={data.color} />
<text x={width+120} y={initialY+30} class="bar-label">{data.reliability.get(year)}%</text>

<style>
    .line-label {
        font-size: 32px;
    }

    .bar-label {
        font-size: 32px;
    }
</style>