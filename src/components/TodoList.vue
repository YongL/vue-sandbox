<template>
	<div>
		<!-- <BaseInputText 
			v-model="newTodoText"
			placeholder="New todo"
			@keydown.enter="addTodo"
		/> -->
        <input
            v-model="newTodoText"
            v-on:keyup.enter="addTodo"
            placeholder="Add a Patient"
        >
		<ul v-if="todos.length">
			<TodoListItem
				v-for="todo in todos"
				:key="todo.id"
				:todo="todo"
				@remove="removeTodo"
			/>
		</ul>
		<p v-else>
			Nothing left in the list. Add a new Patient in the input above.
		</p>
	</div>
</template>

<script>
import BaseInputText from './BaseInputText.vue'
import TodoListItem from './TodoListItem.vue'

let nextTodoId = 1

export default {
	components: {
		BaseInputText, TodoListItem
	},
  data () {
    return {
	    newTodoText: '',
        todos: [
				{
					id: nextTodoId++,
					text: 'Yong Leafen'
				},
				{
					id: nextTodoId++,
					text: 'Adarsh Saxena'
				},
				{
					id: nextTodoId++,
					text: 'Edris Mohsin'
				}
            ]
    }
  },
	methods: {
		addTodo () {
			const trimmedText = this.newTodoText.trim()
			if (trimmedText) {
				this.todos.push({
					id: nextTodoId++,
					text: trimmedText
				})
				this.newTodoText = ''
			}
		},
		removeTodo (idToRemove) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
		}
	}
}
</script>