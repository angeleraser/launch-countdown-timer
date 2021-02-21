<template>
	<div class="countdown-card-wrapper">
		<div class="countdown-card">
			<span class="with-opacity cap"></span>
			<span class="time">{{ cardCount }}</span>
			<span class="cap no-opacity"></span>
		</div>
		<span class="title">{{ cardTitle }}</span>
	</div>
</template>

<script>
export default {
	name: 'CountdownCard',
	props: {
		cardTitle: {
			type: String,
			required: true,
		},
		cardCount: {
			type: Number,
			required: true,
		},
	},
};
</script>

<style scoped>
.countdown-card-wrapper {
	position: relative;
}

.countdown-card {
	align-items: center;
	background-color: var(--dark-desaturated-blue);
	border-radius: 8px;
	box-shadow: 0 8px 6px rgba(0, 0, 0, 0.2);
	color: var(--soft-red);
	display: flex;
	overflow: hidden;
	font-weight: var(--fw-bold);
	height: 100%;
	justify-content: center;
	position: relative;
	width: 100%;
}

.countdown-card .cap {
	height: 50%;
	left: 0;
	position: absolute;
	width: 100%;
}

.countdown-card .cap.with-opacity {
	background-color: var(--very-dark-blue-secondary);
	opacity: 0.2;
	top: 0;
}

.cap.no-opacity {
	bottom: 0;
}

.cap.no-opacity::after,
.cap.no-opacity::before {
	content: '';
	display: inline-block;
	width: 0.5em;
	height: 0.5em;
	background-color: var(--very-dark-blue-secondary);
	border-radius: 50%;
	position: absolute;
	top: 0;
}

.cap.no-opacity::before {
	transform: translate(-50%, -0.25em);
	left: 0;
}

.cap.no-opacity::after {
	transform: translate(50%, -0.25em);
	right: 0;
}

.time {
	font-size: 2.6em;
}

.title {
	bottom: -24px;
	color: var(--grayish-blue);
	font-family: var(--ff-red-hat);
	font-size: 8px;
	font-weight: var(--fw-bold);
	left: 50%;
	letter-spacing: 6px;
	position: absolute;
	text-transform: uppercase;
	transform: translateX(-50%);
}

@media screen and (min-width: 768px) {
	.title {
		bottom: -28px;
		font-size: 10px;
	}
}

@media screen and (min-width: 1280px) {
	.title {
		bottom: -32px;
		font-size: 12px;
	}
}
</style>
