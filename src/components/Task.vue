<template>
	<div class="container">
		<div class="task">
			<the-header>To Do App</the-header>
			<TheForm />
			<div class="task-items">
				<ul>
					<TaskItem :task="task" v-for="task in tasks" :key="task.id" @complete-task="completeTask(task)" />
				</ul>
			</div>
			<ClearButtons @clear-completed="$emit('clear-completed')" @clear-all-tasks="$emit('clear-all-tasks')" />
			<PendingTasks :pendingTasks="countPendingTasks" />
		</div>
	</div>
</template>

<script>
import TheHeader from './TheHeader.vue'
import TheForm from './TheForm.vue'
import TaskItem from './TaskItem.vue'
import ClearButtons from './ClearButtons.vue'
import PendingTasks from './PendingTasks.vue'

export default {
	components: { TaskItem, TheHeader, TheForm, ClearButtons, PendingTasks },
	props: ['tasks'],
	emits: ['clear-completed', 'clear-all-tasks'],
	methods: {
		completeTask(task) {
			task.completed = !task.completed
		},
	},
	computed: {
		countPendingTasks() {
			return this.tasks.filter(task => !task.completed).length
		},
	},
}
</script>

<style scoped>
ul {
	list-style: none;
	margin: 0;
	padding: 0;
}
.container {
	max-width: 480px;
	margin: 0 auto;
	padding: 0 15px;
}
.task {
	background: #fff;
	border-radius: 25px;
	padding: 30px;
	box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.1);
}

.task-items {
	padding: 0 10px;
}
</style>
