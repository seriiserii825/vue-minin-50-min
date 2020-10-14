<template>
  <div id="app">
    <h1>Todo application</h1>
    <hr>
    <AddTodo @addTodo="addTodo"></AddTodo>
    <hr>
    <TodoList
        :todos="todos"
        @removeTodo="removeTodo"
    ></TodoList>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  data () {
    return {
      todos: [
        {id: 1, title: 'Buy bread', completed: false},
        {id: 2, title: 'Buy milk', completed: false},
        {id: 3, title: 'Buy meal', completed: false}
      ]
    }
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(item => id !== item.id)
    },
    addTodo (newTodo) {
      // console.log(newTodo)
      this.todos.push(newTodo)
    }
  },
  components: {
    AddTodo,
    TodoList
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  margin: 0 auto;
  max-width: 600px;
}
</style>
