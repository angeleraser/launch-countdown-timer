<template>
	<div id="app">
		<h1>Hello world</h1>
	</div>
</template>

<script>
import '@/assets/styles/App.css';

export default {
	name: 'App',
	components: {},
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
