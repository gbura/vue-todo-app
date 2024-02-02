<template>
	<div id="app">
		<task :tasks="tasks" @clear-all-tasks="clearAllTasks" @clear-completed="clearCompleted"></task>
	</div>
</template>

<script>
import Task from './components/Task.vue'

export default {
	components: { Task },
	provide() {
		return {
			deleteTask: this.deleteTask,
			tasks: this.tasks,
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

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body {
	font: 15px/1.4 'Poppins', sans-serif;
	background: #4ec5c1;
	color: #333;
}

#app {
	padding: 60px 0;
}

button {
	cursor: pointer;
	font: 15px/1.4 'Poppins', sans-serif;
	color: #555;
	transition: all 0.3s linear;
}

button:focus {
	outline: none;
}
</style>
