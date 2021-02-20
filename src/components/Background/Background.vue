<template>
	<div class="app-background">
		<div id="particles-js"></div>
		<!-- App content -->
		<div class="content">
			<slot></slot>
		</div>

		<!-- Pattern Hills SVG -->
		<img
			src="@/assets/images/svg/pattern-hills.svg"
			alt="Pattern hills background"
			class="pattern-hills"
		/>
	</div>
</template>

<script>
import 'particles.js';
import particlesConfig from '@/assets/particles-config/particles.js';
export default {
	name: 'AppBackground',
	props: ['name', 'lastname'],
	mounted() {
		// eslint-disable-next-line no-undef
		particlesJS('particles-js', particlesConfig);
	},
};
</script>

<style scoped>
.app-background {
	background-color: var(--background);
	height: 100%;
	min-height: 100vh;
	overflow: hidden;
	position: relative;
	width: 100%;
	z-index: 10;
}

.app-background .content {
	align-items: flex-start;
	display: flex;
	justify-content: center;
	min-height: 100vh;
	width: 100%;
	z-index: 50;
}

.app-background img {
	bottom: 0;
	display: block;
	height: 197px;
	left: -50%;
	min-width: 1440px;
	position: absolute;
	transform: translateX(-46%);
}

.app-background #particles-js {
	height: 100%;
	margin: 0 auto;
	min-height: 100vh;
	min-width: 100vw;
	position: fixed;
	top: 0;
	width: 100%;
	z-index: -1;
}

@media screen and (min-width: 480px) {
	.app-background img {
		left: 0;
	}
}

@media screen and (min-width: 768px) {
	.app-background img {
		min-width: 100%;
		transform: translateX(0);
	}
}

@media screen and (min-width: 1366px) {
	.app-background img {
		width: 100%;
		height: auto;
	}
}
</style>
