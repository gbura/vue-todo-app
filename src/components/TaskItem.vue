<template>
	<li>
		<button @click="$emit('complete-task')" :class="completeTask">{{ task.title }}</button>
		<!-- do poprawy, bo nie działa -->
		<button @click="$emit('delete-task', task.id)"><i class="far fa-trash-alt"></i></button>
	</li>
</template>

<script>
export default {
	props: ['task'],
	computed: {
		completeTask() {
			let classes = ['toggle']
			if (this.task.completed) {
				classes.push('toggle-completed')
			}
			return classes
		},
	},
}
</script>
