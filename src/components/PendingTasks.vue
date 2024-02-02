<template>
	<div class="pending-tasks">
		<span>Pending Tasks: {{ pendingTasks }}</span>
	</div>
</template>

<script>
export default {
	props: ['pendingTasks'],
}
</script>

<style scoped>
.pending-tasks {
	padding: 0 6px;
}
</style>
