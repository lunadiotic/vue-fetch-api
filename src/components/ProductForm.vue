<script setup>
import { ref } from 'vue';
import axios from 'axios';

const emit = defineEmits(['add-product']);
const fetchData = () => {
	emit('add-product');
};

const showForm = ref(false);
const newProduct = ref({
	title: '',
	description: '',
	price: '',
	image: '',
});

function showAddForm() {
	showForm.value = true;
}

function closeForm() {
	showForm.value = false;
}

async function addProduct() {
	try {
		const response = await axios.post(
			'http://localhost:3000/products',
			newProduct.value
		);
		console.log('Product added:', response.data);
		// Clear the form and close it after adding the product
		Object.keys(newProduct.value).forEach((key) => {
			newProduct.value[key] = '';
		});
		showForm.value = false;
		// Fetch data again to update the product list
		fetchData();
	} catch (error) {
		console.error('Error adding product:', error);
	}
}
</script>

<template>
	<div class="add-product">
		<button @click="showAddForm">Add Product</button>
		<div v-if="showForm" class="product-form">
			<form @submit.prevent="addProduct">
				<label for="title">Title:</label>
				<input type="text" id="title" v-model="newProduct.title" required />
				<label for="description">Description:</label>
				<input
					type="text"
					id="description"
					v-model="newProduct.description"
					required
				/>
				<label for="price">Price:</label>
				<input type="number" id="price" v-model="newProduct.price" required />
				<label for="image">Image:</label>
				<input type="text" id="image" v-model="newProduct.image" required />
				<button type="submit">Add</button>
				<button type="button" @click="closeForm">Close</button>
			</form>
		</div>
	</div>
</template>

<style scoped>
.add-product {
	text-align: center;
	margin-top: 20px;
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 10px;
	margin-bottom: 20px;
}

.add-product button {
	padding: 10px 20px;
	margin-top: 10px;
	background-color: #28a745;
	color: #fff;
	border: none;
	border-radius: 5px;
	cursor: pointer;
	transition: background-color 0.3s, transform 0.2s;
}

.add-product button:hover {
	background-color: #218838;
	transform: translateY(-2px);
}

.add-product button:focus {
	outline: none;
}

.add-product button:active {
	transform: translateY(1px);
	background-color: #1e7e34;
}

.product-form {
	margin-top: 20px;
	background-color: #f9f9f9;
	border-radius: 8px;
	padding: 20px;
	box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
	max-width: 400px;
	margin: 0 auto;
	text-align: left;
}

.product-form label {
	display: block;
	margin-bottom: 5px;
}

.product-form input[type='text'],
.product-form input[type='number'] {
	width: calc(100% - 20px);
	padding: 8px;
	margin-bottom: 10px;
	border: 1px solid #ccc;
	border-radius: 5px;
}

.product-form button {
	padding: 10px 20px;
	margin-top: 10px;
	background-color: #007bff;
	color: #fff;
	border: none;
	border-radius: 5px;
	cursor: pointer;
	transition: background-color 0.3s;
}

.product-form button:hover {
	background-color: #0056b3;
}

.product-form button[type='submit'] {
	background-color: #28a745;
}

.product-form button[type='submit']:hover {
	background-color: #218838;
}

.product-form button[type='button'] {
	background-color: #dc3545;
}

.product-form button[type='button']:hover {
	background-color: #c82333;
}
</style>
