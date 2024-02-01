<script setup>
import { ref, watchEffect } from 'vue';
import axios from 'axios';

import Pagination from '@/components/Pagination.vue';
import ProductCard from '@/components/ProductCard.vue';
import Loading from '@/components/Loading.vue';

const products = ref([]);
const page = ref(1);
const limit = ref(8);
const isLoading = ref(true);

const fetchData = async () => {
	const API_URL = `http://localhost:3000/products?_page=${page.value}&_per_page=${limit.value}`;
	try {
		const response = await axios.get(API_URL);
		return response.data;
	} finally {
		isLoading.value = false;
	}
};

watchEffect(() => {
	isLoading.value = true;
	fetchData().then((data) => {
		products.value = data;
	});
});

const changePage = (newPage) => {
	if (newPage < 1) {
		newPage = 1;
	}
	if (newPage > products.value.pages) {
		newPage = products.value.pages;
	}
	page.value = newPage;
};
</script>

<template>
	<main>
		<div v-if="isLoading">
			<Loading />
		</div>
		<div v-else>
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
		</div>
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
