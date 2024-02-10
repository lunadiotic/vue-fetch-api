<script setup>
const props = defineProps({
	page: Number,
	totalPages: Number,
});

const emit = defineEmits(['change-page']);

function changePage(newPage) {
	emit('change-page', newPage);
}
</script>

<template>
	<!-- create button first -->
	<div v-show="page > 1">
		<button class="pagination-button" id="firstPage" @click="changePage(1)">
			&lt;&lt;
		</button>
		<button
			class="pagination-button"
			id="prevPage"
			@click="changePage(page - 1)"
			v-show="page > 1"
		>
			&lt;
		</button>
	</div>
	<span>Page {{ page }} of {{ totalPages }}</span>
	<div v-show="page < totalPages">
		<button
			class="pagination-button"
			id="nextPage"
			@click="changePage(page + 1)"
		>
			&gt;
		</button>
		<!-- create button last -->
		<button
			class="pagination-button"
			id="lastPage"
			@click="changePage(totalPages)"
		>
			&gt;&gt;
		</button>
	</div>
</template>

<style scoped>
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
