<script context="module">
	export function preload() {
		console.log('/one/two/_layout.svelte preload fired')
		return {}
	}
</script>

<slot></slot>