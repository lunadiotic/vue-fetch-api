<script setup>
import {
	onBeforeMount,
	onBeforeUnmount,
	onBeforeUpdate,
	onMounted,
	onUnmounted,
	onUpdated,
	ref,
} from 'vue';

const greeting = ref('Hello');

function changeGreeting() {
	greeting.value = 'Goodbye';
}

onBeforeMount(() => {
	console.log('Component will be mounted soon');
	// Lakukan persiapan atau efek samping sebelum mounting
});

onMounted(() => {
	console.log('Component has been mounted');
	// Lakukan tugas setelah mounting, seperti fetching data
});

onBeforeUpdate(() => {
	console.log('Component will be updated soon');
	// Lakukan persiapan atau efek samping sebelum pembaruan
});

onUpdated(() => {
	console.log('Component has been updated');
	// Lakukan tugas setelah pembaruan, jika diperlukan
});

onBeforeUnmount(() => {
	console.log('Component will be unmounted soon');
	// Lakukan pembersihan atau persiapan sebelum unmounting
});

onUnmounted(() => {
	console.log('Component has been unmounted');
	// Lakukan tugas terakhir sebelum dihapus
});
</script>

<template>
	<div>
		<h1>About</h1>
		<p>{{ greeting }}</p>
		<button @click="changeGreeting">Change greeting</button>
	</div>
</template>
