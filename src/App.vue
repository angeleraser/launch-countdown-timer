<template>
	<div id="app">
		<app-background>
			<app-countdown
				@increaseYear="updateDateYear"
				:startDate="startDate"
				:endDate="endDate"
			/>
			<app-footer />
		</app-background>
	</div>
</template>

<script>
import '@/assets/styles/App.css';
import AppBackground from '@/components/Background/Background';
import AppCountdown from './components/Countdown/Countdown.vue';
import AppFooter from '@/components/Footer/Footer.vue';

export default {
	name: 'App',
	components: { AppBackground, AppCountdown, AppFooter },
	data() {
		return {
			startDate: new Date(),
			endDate: new Date(2022, 9, 9, 0),
		};
	},
	methods: {
		updateDateYear(newDate) {
			this.endDate = newDate;
		},
	},
};
</script>

<style>
#app {
	align-items: flex-start;
	display: flex;
	flex-direction: column;
	font-size: var(--fs-base);
	font-family: var(--ff-red-hat);
	min-height: 100vh;
	min-width: 360px;
	width: 100%;
}
</style>
