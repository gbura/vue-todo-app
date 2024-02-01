<template>
	<div class="container">
		<div class="task">
			<!-- title -->
			<div class="title">
				<h1>To Do List</h1>
			</div>
			<!-- form -->
			<div class="form">
				<input type="text" placeholder="New Task" v-model.trim="newTask" @keyup.enter="addTask" />
				<button @click="addTask"><i class="fas fa-plus"></i></button>
			</div>
			<!-- task lists -->
			<div class="taskItems">
				<ul>
					<task-item :task="task" v-for="task in tasks" :key="task.id" @complete-task="completeTask(task)"> </task-item>
				</ul>
			</div>
			<!-- buttons -->
			<div class="clearBtns">
				<button @click="$emit('clear-completed')">Clear completed</button>
				<button @click="$emit('clear-all-tasks')">Clear all</button>
			</div>
			<!-- pending task -->
			<div class="pendingTasks">
				<span>Pending Tasks: {{ isPending.length }}</span>
			</div>
		</div>
	</div>
</template>

<script>
import TaskItem from './TaskItem.vue'

export default {
	name: 'Task',
	components: { TaskItem },
	props: ['tasks'],
	data() {
		return {
			newTask: '',
		}
	},
	computed: {
		isPending() {
			return this.tasks.filter(task => !task.completed)
		},
	},
	methods: {
		addTask() {
			this.tasks.push({
				id: this.tasks.length + 1,
				title: this.newTask,
				completed: false,
			})
			this.newTask = ''
		},
		completeTask(task) {
			task.completed = !task.completed
		},
	},
}
</script>
