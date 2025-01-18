<script lang="ts">
	let { children } = $props();
    export const prerender = true;
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