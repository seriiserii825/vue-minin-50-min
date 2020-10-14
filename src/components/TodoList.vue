<template>
  <div>
    <ul>
      <TodoItem
          :key="todo.id"
          v-for="(todo, index) in todos"
          :index="index"
          :todo="todo"
          @removeTodo="removeTodo"
      ></TodoItem>
    </ul>
  </div>
</template>
<script>

import TodoItem from './TodoItem'

export default {
  props: ['todos'],
  methods: {
    removeTodo (id) {
      return this.$emit('removeTodo', id)
    }
  },
  components: {
    TodoItem
  }
}
</script>

<style scoped>
ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}
</style>
