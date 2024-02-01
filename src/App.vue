<script setup>
import { RouterView } from 'vue-router';
import Home from './views/Home.vue';
</script>

<template>
	<!-- <RouterLink to="/">Home</RouterLink>
	<RouterLink to="/About">About</RouterLink> -->
	<RouterView />
	<!-- <Suspense>
		<template #default> <Home /> </template>
		<template #fallback> Loading... </template>
	</Suspense> -->
</template>

<style scoped></style>
