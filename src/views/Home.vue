<script setup>
import { ref, watch } from 'vue';
import axios from 'axios';

import Pagination from '@/components/Pagination.vue';
import ProductCard from '@/components/ProductCard.vue';

const products = ref([]);
const page = ref(1);
const limit = ref(8);
const API_URL = `http://localhost:3000/products?_page=${page.value}&_per_page=${limit.value}`;

products.value = await axios.get(API_URL).then((res) => res.data);

watch(page, async () => {
	products.value = await axios.get(API_URL).then((res) => res.data);
	console.log('fetch');
});

function changePage(newPage) {
	if (newPage < 1) {
		newPage = 1;
	}
	if (newPage > products.value.pages) {
		newPage = products.value.pages;
	}
	page.value = newPage;
}

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
				v-for="product in products.data"
				:key="product.id"
				:product="product"
			/>
		</div>
		<Pagination
			:page="page"
			:totalPages="products.pages"
			@change-page="changePage"
		/>
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
