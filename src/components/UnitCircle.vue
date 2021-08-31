<template>
	<svg
		@mousemove="getPosition($event)"
		version="1.1"
		baseProfile="full"
		width="500"
		height="500"
		xmlns="http://www.w3.org/2000/svg"
	>
		<circle cx="250" cy="250" r="100" />
		<line class="dashed" x1="0" y1="250" x2="500" y2="250" />
		<line class="dashed" x1="250" y1="0" x2="250" y2="500" />
	</svg>
</template>

<script>
	export default {
		name: 'UnitCircle',
	};
</script>

<style scoped>
	svg {
		border: var(--fg) 3px solid;
	}
	circle {
		fill: none;
		stroke: var(--fg);
		stroke-width: 5px;
	}
	line {
		stroke: var(--fg);
		stroke-width: 5px;
	}
</style>
