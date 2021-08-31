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

		<!-- __ COS __ -->
		<line x1="0" y1="250" x2="500" y2="250" />
		<line id="cos" x1="250" y1="250" :x2="cosLength" y2="250" />
		<!-- --------- -->

		<!-- __ SIN __ -->
		<line x1="250" y1="0" x2="250" y2="500" />
		<line id="sin" x1="250" y1="250" x2="250" :y2="sinLength" />
		<!-- --------- -->

		<!-- -- angle line -- -->
		<line x1="250" y1="250" :x2="endOfLine.x" :y2="endOfLine.y" />
		<!-- ---------------- -->
		<!-- position relative to svg fix -->
		<rect width="500" height="500" />
	</svg>
</template>

<script>
	export default {
		name: 'UnitCircle',
		data() {
			return {
				mousePosition: {
					x: 0,
					y: 0,
				},
			};
		},
		computed: {
			// mouse position relative to the center of the graph
			a() {
				return this.mousePosition.x - 250;
			},
			b() {
				return this.mousePosition.y - 250;
			},

			endOfLine() {
				let x, y;
				let a = this.a,
					b = this.b;

				x = a < 0 ? 0 : 500;
				y = b < 0 ? 0 : 500;

				if (Math.abs(a) > Math.abs(b)) {
					y = Math.round((b * 250) / Math.abs(a)) + 250;
				} else if (Math.abs(a) < Math.abs(b)) {
					x = Math.round((a * 250) / Math.abs(b)) + 250;
				}

				return { x: x, y: y };
			},

			angle() {
				let baseAng = -Math.atan2(this.b, this.a);
				return baseAng < 0 ? baseAng + 2 * Math.PI : baseAng;
			},

			cosLength() {
				return 100 * Math.cos(this.angle) + 250;
			},
			sinLength() {
				return -100 * Math.sin(this.angle) + 250;
			},
		},
		methods: {
			getPosition(e) {
				// update mouse position props
				let rect = e.target.getBoundingClientRect();
				this.mousePosition = {
					x: e.clientX - rect.left,
					y: e.clientY - rect.top,
				};
			},
		},
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
		stroke-linecap: round;
	}

	rect {
		opacity: 0;
	}

	#cos,
	#sin,
	#tg,
	#cotg {
		stroke-width: 6px;
	}

	#cos {
		stroke: var(--sin);
	}

	#sin {
		stroke: var(--cos);
	}

	#tg {
		stroke: var(--tg);
	}

	#cotg {
		stroke: var(--cotg);
	}
</style>
