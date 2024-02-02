<template>
	<div class="form">
		<input type="text" placeholder="New Task" v-model.trim="newTask" @keyup.enter="addTask" />
		<button @click="addTask"><i class="fas fa-plus"></i></button>
	</div>
</template>

<script>
export default {
	inject: ['tasks'],
	data() {
		return {
			newTask: '',
		}
	},
	methods: {
		addTask() {
			if (this.validate()) {
				this.tasks.push({
					id: this.tasks.length + 1,
					title: this.newTask,
					completed: false,
				})
				this.newTask = ''
			}
		},
		validate() {
			if (this.newTask === '') {
				return false
			}
			return true
		},
	},
}
</script>

<style scoped>
input[type='text'] {
	width: 100%;
	height: 50px;
	font: 15px/1.4 'Poppins', sans-serif;
	padding: 15px;
	background: #f3f3f3;
	color: #333;
	border: 1px solid transparent;
	border-radius: 10px;
	transition: border 0.3s linear;
}

input[type='text']:focus {
	outline: none;
	border: 1px solid #4ec5c1;
}

.form {
	position: relative;
	margin: 0 0 30px;
}

.form button {
	background: none;
	border: none;
	color: #4ec5c1;
	font-size: 18px;
	position: absolute;
	top: 50%;
	right: 20px;
	transform: translateY(-50%);
}
</style>
