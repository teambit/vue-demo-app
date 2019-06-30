<template>
	<div>
		<TodoInputControls 
			placeholder="Insert a task"
			@onAdd="addTodo"
		/>
		<ul v-if="todos.length" class="list-group">
			<transition-group name="fade">
				<TodoListItem
					v-for="todo in todos"
					:key="todo.id"
					:todo="todo"
					@remove="removeTodo"
				/>
			</transition-group>
		</ul>
		<p v-else-if="isNewList">
			Add a new task to the list!
		</p>
		<p v-else>
			All done! No more tasks to complete.
		</p>
	</div>
</template>

<script>
import TodoInputControls from './TodoInputControls.vue'
import TodoListItem from './TodoListItem.vue'

let nextTodoId = 1

export default {
	components: {
		TodoInputControls, TodoListItem
	},
  data () {
    return {
	  todos: [],
	  isNewList: true
    }
  },
	methods: {
		addTodo (value) {
			if (this.isNewList) {this.isNewList = false};
			this.todos.push({
				id: nextTodoId++,
				text: value
			})
		},
		removeTodo (idToRemove) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
		}
	}
}
</script>

<style>

.fade-enter {
	opacity: 0;
}

.fade-enter-active {
	transition: opacity 0.75s;
}


.fade-leave-active{
	transition: opacity 0.75s;
	opacity: 0;
}
</style>
