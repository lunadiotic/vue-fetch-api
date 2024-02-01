<template>
	<div class="product-card">
		<img src="" alt="Product 1" class="product-image" />
		<h2 class="product-title">Product 1</h2>
		<p class="product-description">Short description for Product 1.</p>
		<span class="product-price">Rp 100.000</span>
	</div>
</template>

<style scoped>
.product-card {
	background-color: #fff;
	padding: 20px;
	border-radius: 8px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	transition: transform 0.3s ease-in-out;
	cursor: pointer;
}

.product-card:hover {
	transform: scale(1.05);
}

.product-image {
	width: 100%;
	height: 150px;
	object-fit: cover;
	border-radius: 4px;
	margin-bottom: 10px;
}

.product-title {
	font-size: 18px;
	font-weight: bold;
	margin-bottom: 10px;
}

.product-description {
	color: #555;
	margin-bottom: 10px;
}

.product-price {
	color: #00b894;
	font-weight: bold;
}
</style>
