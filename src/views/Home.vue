<script setup>
import Pagination from '@/components/Pagination.vue';
import ProductCard from '@/components/ProductCard.vue';

import {
	onBeforeMount,
	onBeforeUnmount,
	onBeforeUpdate,
	onMounted,
	onUnmounted,
	onUpdated,
	ref,
} from 'vue';

const page = ref(1);

function nextPage() {
	page.value++;
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
	<main>
		{{ page }}
		<div class="product-grid">
			<ProductCard />
		</div>
		<Pagination />
		<button @click="nextPage">Next</button>
	</main>
</template>

<style scoped>
.product-grid {
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
	gap: 20px;
	width: 80%;
	margin: 0 auto;
}
</style>
