<template>
	<div id="app">
		<task
			:tasks="tasks"
			@clear-all-tasks="clearAllTasks"
			@clear-completed="clearCompleted"
			@delete-task="deleteTask"></task>
	</div>
</template>

<script>
import Task from './components/Task.vue'

export default {
	name: 'App',
	components: {
		Task,
	},
	data() {
		return {
			tasks: [],
		}
	},
	methods: {
		clearAllTasks() {
			this.tasks = []
		},
		clearCompleted() {
			this.tasks = this.tasks.filter(task => !task.completed)
		},
		deleteTask(id) {
			this.tasks = this.tasks.filter(task => task.id !== id)
		},
	},
}
</script>
