<template>
  <li>
    <span :class="{done: todo.completed}">
      <input type="checkbox" @change="todo.completed = !todo.completed">
      <strong>{{ index + 1 }}</strong>
      <span>{{ todo.title }}</span>
    </span>
    <button class="rm" @click="$emit('removeTodo', todo.id)">&times;</button>
  </li>
</template>
<script>
export default {
  props: ['todo', 'index']
}
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  margin-bottom: .5rem;
  padding: .5rem .2rem;
  border: 1px solid #ccc;
  transition: all .3s;
}
li:hover {
  background-color: #eee;
  cursor: pointer;
}
.rm {
  font-weight: bold;
  color: white;
  background-color: red;
  border-radius: 50%;
  border: none;
}
.done {
  text-decoration: line-through;
}
input {
  margin-right: 1rem;
}
</style>
