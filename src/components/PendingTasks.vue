<template>
	<div class="pending-tasks">
		<span>Pending Tasks: {{ isPending }}</span>
	</div>
</template>

<script>
export default {
	props: ['isPending'],
}
</script>

<style scoped>
.pending-tasks {
	padding: 0 6px;
}
</style>
