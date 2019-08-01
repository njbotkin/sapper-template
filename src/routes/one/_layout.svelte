<script context="module">
	export function preload() {
		console.log('/one/_layout.svelte preload fired')
		return {}
	}
</script>

<slot></slot>