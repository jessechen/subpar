<script lang="ts">
    export let name: string;
    export let x: number;
    export let y: number;
    export let width: number;
    export let height: number;
    export let color: string;
</script>

<rect id={name} {x} {y} {width} {height} fill={color} />