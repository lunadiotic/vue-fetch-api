<script setup>
import { ref } from 'vue';
import axios from 'axios';

import Pagination from '@/components/Pagination.vue';
import ProductCard from '@/components/ProductCard.vue';

const products = ref([]);

products.value = await axios
	.get('http://localhost:3000/products')
	.then((res) => res.data);

// async function fetchData() {
// 	const response = await axios.get('http://localhost:3000/products');
// 	products.value = response.data;
// 	console.log(products.value);
// }

// fetchData();
</script>

<template>
	<main>
		<div class="product-grid">
			<ProductCard
				v-for="product in products"
				:key="product.id"
				:product="product"
			/>
		</div>
		<Pagination />
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
