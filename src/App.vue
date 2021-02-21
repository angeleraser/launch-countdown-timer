<template>
	<div id="app">
		<app-background>
			<countdown-container />
			<app-footer />
		</app-background>
	</div>
</template>

<script>
import '@/assets/styles/App.css';
import AppBackground from '@/components/Background/Background';
import CountdownContainer from './components/Countdown/Countdown.vue';
import AppFooter from '@/components/Footer/Footer.vue';

export default {
	name: 'App',
	components: { AppBackground, CountdownContainer, AppFooter },
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
