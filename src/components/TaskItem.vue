<template>
	<li>
		<button @click="$emit('complete-task')" :class="completedTaskClass">{{ task.title }}</button>
		<button @click="deleteProvidedTask"><i class="far fa-trash-alt"></i></button>
	</li>
</template>

<script>
export default {
	props: ['task'],
	inject: ['deleteTask'],
	emits: ['complete-task'],
	computed: {
		completedTaskClass() {
			let classes = ['toggle']
			if (this.task.completed) {
				classes.push('toggle-completed')
			}
			return classes
		},
	},
	methods: {
		deleteProvidedTask() {
			this.deleteTask(this.task.id)
		},
	},
}
</script>

<style scoped>
.task-items li {
	display: flex;
	justify-content: space-between;
	margin: 0 0 20px;
}

.task-items button {
	background: none;
	border: none;
}

.task-items button:hover {
	color: #4ec5c1;
}

.task-items .toggle i {
	margin: 0 10px 0 0;
	font-size: 14px;
}

.task-items .toggle.toggle-completed {
	text-decoration: line-through;
}
</style>
