<template>
	<div id="app">
		<app-background>Hola</app-background>
	</div>
</template>

<script>
import '@/assets/styles/App.css';
import AppBackground from '@/components/Background/Background';

export default {
	name: 'App',
	components: { AppBackground },
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
