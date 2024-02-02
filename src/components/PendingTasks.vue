<template>
	<div class="pending-tasks">
		<span>Pending Tasks: {{ isPending }}</span>
	</div>
</template>

<script>
export default {
	inject: ['tasks'],
	computed: {
		isPending() {
			return this.tasks.filter(task => !task.completed).length
		},
	},
}
</script>

<style scoped>
.pending-tasks {
	padding: 0 6px;
}
</style>
