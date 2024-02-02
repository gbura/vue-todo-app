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
