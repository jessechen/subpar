<script lang="ts">
    let { data, index, year } = $props();
    const width = $derived((data.reliability.get(year) || 0) * 8);
</script>

<rect id={data.name} x=0 y={index*50} {width} height=40 fill={data.color} />
<text x={width+20} y={index*50+30} class="bar-label">{data.name} - {data.reliability.get(year)}%</text>

<style>
    .bar-label {
        font-size: 32px;
    }
</style>