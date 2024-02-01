<template>
	<div class="pagination">
		<button class="pagination-button" id="prevPage">&lt;</button>
		<button class="pagination-button" id="nextPage">&gt;</button>
	</div>
</template>

<style scoped>
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
