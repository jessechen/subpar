<script lang="ts">
    let { data, index, year } = $props();
    const width = $derived((data.reliability.get(year) || 0) * 10);
</script>

<rect id={data.name} x=0 y={index*100} {width} height=80 fill={data.color} />