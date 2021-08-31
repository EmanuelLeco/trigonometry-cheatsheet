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
		--sin: #3cc386;
		--cos: #433cc3;
		--tg: #c33c79;
		--cotg: #bcc33c;

		--fg: #324d7e;
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
