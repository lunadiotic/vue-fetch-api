<script setup>
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';
import axios from 'axios';
import ProductForm from '@/components/ProductForm.vue';

const props = defineProps({
	id: {
		type: String,
		required: true,
	},
});

const router = useRouter();
const product = ref({});
const API_URL = `http://localhost:3000/products/${props.id}`;

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
		<p>Description: {{ product.description }}</p>
		<p>Price: {{ product.price }}</p>
		<product-form :product="product" @update-product="updateProduct" />
		<router-link to="/" class="back-button">Back</router-link>
		<button @click="deleteProduct" class="delete-button">Delete</button>
	</div>
</template>

<style scoped>
/* Styling untuk halaman detail produk */
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

.back-button {
	display: inline-block;
	padding: 8px 16px;
	background-color: #007bff;
	color: #fff;
	text-decoration: none;
	border: none;
	border-radius: 4px;
	transition: background-color 0.3s;
}

.back-button:hover {
	background-color: #0056b3;
}

.delete-button {
	display: inline-block;
	padding: 8px 16px;
	background-color: #dc3545;
	color: #fff;
	text-decoration: none;
	border: none;
	border-radius: 4px;
	transition: background-color 0.3s;
}

.delete-button:hover {
	background-color: #c82333;
	cursor: pointer;
}
</style>
