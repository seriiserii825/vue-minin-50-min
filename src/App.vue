<template>
  <div id="app">
    <h1>Todo application</h1>
    <hr>
    <AddTodo @addTodo="addTodo"/>
    <hr>
    <TodoList
      :todos="todos"
      @removeTodo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  data () {
    return {
      todos: [],
      resource: null,
      resourceDelete: null
    }
  },
  methods: {
    removeTodo (id) {
      this.resourceDelete.delete({id: id})
        .then(response => {
          console.log('deleted ' + id)
        })
    },
    addTodo (newTodo) {
      if (newTodo.title !== '') {
        this.resource.save(newTodo)
          .then(response => response.json())
          .then(todos => {
            console.log(todos)
          })
      }
    },
    loadResource () {
      this.resource.get()
        .then(response => response.json())
        .then(todos => {
          this.todos = todos
        })
    }
  },
  components: {
    AddTodo,
    TodoList
  },
  created () {
    this.resource = this.$resource('todos')
    this.loadResource()
  },
  updated () {
    this.resource = this.$resource('todos')
    this.resourceDelete = this.$resource('todos{/id}')
    this.loadResource()
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
