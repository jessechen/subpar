<script lang="ts">
    export const prerender = true;
	let { children } = $props();
</script>

{@render children?.()}

<style>
	:global(body) {
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		align-items: center;
		font-family: Seravek, 'Gill Sans Nova', Ubuntu, Calibri, 'DejaVu Sans', source-sans-pro, sans-serif;
	}
</style>