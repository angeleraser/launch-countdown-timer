<template>
	<div class="countdown-container">
		<h1 class="heading">We're launching soon</h1>
		<div class="countdown-cards">
			<countdown-card
				v-for="name in countdownCardsTitles"
				:key="name"
				:cardTitle="name"
			/>
		</div>
	</div>
</template>

<script>
import CountdownCard from '../CountdownCard/CountdownCard.vue';
export default {
	components: { CountdownCard },
	name: 'CountdownContainer',
	data() {
		return {
			countdownCardsTitles: ['days', 'hours', 'minutes', 'seconds'],
		};
	},
};
</script>

<style scoped>
.countdown-container {
	align-items: center;
	display: flex;
	flex-direction: column;
	padding: 146px 26px 48px;
	font-size: 16px;
	width: 100%;
}

h1 {
	color: var(--white);
	font-family: var(--ff-red-hat);
	font-size: 16px;
	font-weight: var(--fw-bold);
	letter-spacing: 10px;
	line-height: 1.5;
	margin-bottom: 60px;
	text-align: center;
	text-transform: uppercase;
}

.countdown-cards {
	display: grid;
	font-size: 3.3vw;
	grid-template-columns: repeat(4, 5.8em);
	grid-template-rows: 5.5em;
	max-width: 688px;
	place-content: space-between;
	width: 100%;
}

@media screen and (min-width: 768px) {
	.countdown-cards {
		font-size: 2.3vw;
	}
}

@media screen and (min-width: 1280px) {
	.countdown-cards {
		font-size: 26px;
	}
}
</style>
