<template>
	<div class="app-background">
		<div class="content">
			<slot></slot>
		</div>
		<img
			src="@/assets/images/svg/pattern-hills.svg"
			alt="Pattern hills background"
			class="pattern-hills"
		/>
	</div>
</template>

<script>
export default {
	name: 'AppBackground',
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
}

.app-background .content {
	min-height: 100vh;
	width: 100%;
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
