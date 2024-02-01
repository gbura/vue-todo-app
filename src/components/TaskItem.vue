<template>
	<li>
		<button @click="$emit('complete-task')" :class="completedTaskClass">{{ task.title }}</button>
		<button @click="$emit('delete-task', task.id)"><i class="far fa-trash-alt"></i></button>
	</li>
</template>

<script>
export default {
	props: ['task'],
	computed: {
		completedTaskClass() {
			let classes = ['toggle']
			if (this.task.completed) {
				classes.push('toggle-completed')
			}
			return classes
		},
	},
}
</script>
