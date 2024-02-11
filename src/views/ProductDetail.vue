<script setup>
import { onMounted, ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import axios from 'axios';
import ProductForm from '@/components/ProductForm.vue';

const route = useRoute();
const router = useRouter();

const id = route.params.id;
const product = ref({});
const API_URL = `http://localhost:3000/products/${id}`;

onMounted(() => {
	fetchData();
});

async function fetchData() {
	try {
		const response = await axios.get(API_URL);
		product.value = response.data;
	} catch (error) {
		console.error(error);
	}
}

async function updateProduct(product) {
	try {
		await axios.put(API_URL, product);
		router.push('/');
	} catch (error) {
		console.error(error);
	}
}

async function deleteProduct() {
	try {
		await axios.delete(API_URL);
		router.push('/');
	} catch (error) {
		console.error(error);
	}
}
</script>

<template>
	<div class="product-detail">
		<h2>{{ product.title }}</h2>
		<img :src="product.image" :alt="product.title" class="product-image" />
		<p>{{ product.description }}</p>
		<p>Rp{{ product.price }}</p>
		<ProductForm :product="product" @update-product="updateProduct" />
		<router-link to="/" class="back-button">Back</router-link>
		<button @click="deleteProduct" class="delete-button">Delete</button>
	</div>
</template>

<style scoped>
.product-detail {
	margin-top: 20px;
	padding: 20px;
	border: 1px solid #ccc;
	border-radius: 5px;
	background-color: #f9f9f9;
	text-align: center;
}

.product-image {
	max-width: 100%;
	height: auto;
	margin-bottom: 10px;
}

.product-detail p {
	margin-bottom: 5px;
}

.product-detail button {
	margin-top: 10px;
	padding: 10px 20px;
	color: #fff;
	border: none;
	border-radius: 5px;
	cursor: pointer;
}

.back-button {
	display: inline-block;
	padding: 8px 16px;
	background-color: #007bff;
	color: #fff;
	text-decoration: none;
	border-radius: 4px;
	transition: background-color 0.3s;
}

.back-button:hover {
	background-color: #0056b3;
}

.delete-button {
	display: inline-block;
	padding: 8px 16px;
	background-color: #ff0000;
	color: #fff;
	text-decoration: none;
	border-radius: 4px;
	transition: background-color 0.3s;
}

.delete-button:hover {
	background-color: #b30000;
}
</style>
