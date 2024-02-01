<script setup>
const props = defineProps({
	page: Number,
	totalPages: Number,
});

const emit = defineEmits(['change-page']);
function changePage(direction) {
	const newPage = props.page + direction;
	emit('change-page', newPage);
}
</script>

<template>
	<div class="pagination">
		<button
			class="pagination-button"
			id="prevPage"
			@click="changePage(-1)"
			v-show="page > 1"
		>
			&lt;
		</button>
		<span>{{ page }}</span>
		<button
			class="pagination-button"
			id="nextPage"
			@click="changePage(1)"
			v-show="page < totalPages"
		>
			&gt;
		</button>
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
