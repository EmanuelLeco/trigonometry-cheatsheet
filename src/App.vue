<template>
	<unit-circle />
</template>

<script>
	import UnitCircle from './components/UnitCircle.vue';
	export default {
		name: 'App',
		components: { UnitCircle },
	};
</script>

<style>
	:root {
		--sin: #6dff79;
		--cos: #6af8d9;
		--tg: #c33c79;
		--cotg: #bcc33c;

		--fg: #6c95e0;
		--bg: #1a263d;
	}

	body {
		margin: 0;
		padding: 0;
		background-color: var(--bg);
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>
