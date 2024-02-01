<script setup></script>

<template>
	<main>
		<div class="product-grid">
			<!-- Product 1 -->
			<div class="product-card">
				<img src="" alt="Product 1" class="product-image" />
				<h2 class="product-title">Product 1</h2>
				<p class="product-description">Short description for Product 1.</p>
				<span class="product-price">Rp 100.000</span>
			</div>

			<!-- Product 2 -->
			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>

			<div class="product-card">
				<img src="" alt="Product 2" class="product-image" />
				<h2 class="product-title">Product 2</h2>
				<p class="product-description">Short description for Product 2.</p>
				<span class="product-price">Rp 150.000</span>
			</div>
		</div>
		<div class="pagination">
			<button class="pagination-button" id="prevPage">&lt;</button>
			<button class="pagination-button" id="nextPage">&gt;</button>
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
.pagination {
	display: flex;
	justify-content: center;
	align-items: center;
	margin-top: 20px;
}

.pagination-button {
	background-color: #fff;
	color: #00b894;
	padding: 8px 12px;
	border: none;
	border-radius: 50%;
	cursor: pointer;
	font-size: 16px;
	margin: 0 5px;
}
</style>
