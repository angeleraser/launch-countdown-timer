<template>
	<div class="countdown-card-wrapper">
		<div :class="classNames" class="countdown-card">
			<span class="with-opacity cap"> </span>
			<span class="time">{{ cardCount }}</span>
			<span class="dots"><div class="line"></div></span>
			<span class="cap no-opacity"></span>
		</div>
		<span class="title">{{ cardTitle }}</span>
	</div>
</template>

<script>
export default {
	name: 'CountdownCard',
	data() {
		return {
			isReverse: false,
		};
	},
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
	watch: {
		cardCount() {
			if (this.cardTitle !== 'seconds') {
				this.isReverse = true;

				const timeout = setTimeout(() => {
					this.isReverse = false;
					clearTimeout(timeout);
				}, 800);
			}
		},
	},
	computed: {
		classNames() {
			return {
				reversed: this.isReverse,
				[`not-reversed`]: !this.isReverse,
			};
		},
	},
	// updated() {
	// 	this.isReverse = true;
	// },
};
</script>

<style scoped>
.countdown-card-wrapper {
	position: relative;
}

.countdown-card {
	align-items: center;
	background-color: transparent;
	border-radius: 8px;
	color: var(--soft-red);
	display: flex;
	font-weight: var(--fw-bold);
	height: 100%;
	justify-content: center;
	position: relative;
	width: 100%;
}

.countdown-card .cap {
	height: 50%;
	background-color: var(--dark-desaturated-blue);
	left: 0;
	position: absolute;
	border-radius: 8px;
	width: 100%;
}

.countdown-card .cap.with-opacity {
	top: 0;
	transform-origin: bottom;
	border-bottom-left-radius: 0;
	border-bottom-right-radius: 0;
	transition: all 0.8s linear;
}

.countdown-card .cap.with-opacity::after {
	background-color: var(--very-dark-blue-secondary);
	border-top-left-radius: 8px;
	border-top-right-radius: 8px;
	content: '';
	height: 100%;
	left: 0;
	opacity: 0.2;
	position: absolute;
	top: 0;
	width: 100%;
}

.countdown-card .cap.no-opacity {
	bottom: 0;
	border-top-left-radius: 0;
	border-top-right-radius: 0;
	box-shadow: 0 8px 6px rgba(0, 0, 0, 0.2);
}

.dots {
	width: 100%;
	height: auto;
	position: absolute;
	z-index: 20;
	overflow-x: hidden;
	transition: all 0.1s linear;
}

.dots .line {
	height: 0.5em;
	width: 100%;
}

.dots::after,
.dots::before {
	content: '';
	display: inline-block;
	width: 0.5em;
	height: 0.5em;
	background-color: var(--very-dark-blue-secondary);
	border-radius: 50%;
	position: absolute;
	top: 50%;
	transform: translateY(-50%);
}

.dots::before {
	transform: translate(-50%, -0.25em);
	left: 0;
}

.dots::after {
	transform: translate(50%, -0.25em);
	right: 0;
}

.time {
	font-size: 2.6em;
	z-index: 10;
	transition: transform 0.8s, opacity 0.2s linear;
	transition-delay: 0.3s;
}

.title {
	bottom: -24px;
	color: var(--grayish-blue);
	font-family: var(--ff-red-hat);
	font-size: 6px;
	font-weight: var(--fw-bold);
	left: 50%;
	letter-spacing: 6px;
	position: absolute;
	text-transform: uppercase;
	transform: translateX(-50%);
	text-align: center;
	width: 100%;
}

.countdown-card.reversed .cap.with-opacity {
	transform: rotateX(180deg);
	z-index: 100;
}

.countdown-card.not-reversed .cap.with-opacity {
	transform: rotateX(0deg);
}

.countdown-card.reversed .cap.with-opacity::after {
	background-color: var(--dark-desaturated-blue);
	opacity: 1;
}

.countdown-card.reversed .dots {
	opacity: 0;
}

.countdown-card.not-reversed {
	opacity: 1;
}

.countdown-card.reversed .time {
	transform: rotateX(180deg);
	opacity: 0;
	transition: opacity 0s;
}

.countdown-card.not-reversed .time {
	transform: rotateX(0deg) rotateY(0deg);
	opacity: 1;
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
