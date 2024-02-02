<template>
	<div class="clear-btns">
		<button @click="$emit('clear-completed')">Clear completed</button>
		<button @click="$emit('clear-all-tasks')">Clear all</button>
	</div>
</template>

<script>
export default {}
</script>

<style scoped>
.clear-btns {
	display: flex;
	justify-content: space-between;
	margin: 0 0 20px;
}

.clear-btns button {
	width: 100%;
	background: #4ec5c1;
	color: #fff;
	border: none;
	border-radius: 10px;
	padding: 10px;
	margin: 0 5px;
}

.clear-btns button:hover {
	background: #333;
}
</style>
