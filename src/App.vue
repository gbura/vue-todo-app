<template>
	<div id="app">
		<task :tasks="tasks" @clear-all-tasks="clearAllTasks" @clear-completed="clearCompleted"></task>
	</div>
</template>

<script>
import Task from './components/Task.vue'

export default {
	components: {
		Task,
	},
	provide() {
		return {
			deleteTask: this.deleteTask,
		}
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
