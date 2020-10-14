<template>
  <form class="add-todo" @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
</template>
<script>
export default {
  data () {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit () {
      if (this.title.trim) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('addTodo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>
<style scoped>
.add-todo {
  display: flex;
  justify-content: space-between;
  margin: 60px auto;
}
input {
  flex: 1;
  display: block;
  padding: 0 15px;
  height: 40px;
  border: 1px solid #ccc;
}
button {
  display: block;
  flex: 0 0 100px;
  height: 40px;
  border: 1px solid #ccc;
  transition: all .3s;
  cursor: pointer;
  background-color: #eee;
}
button:hover {
  background-color: #ccc;
}
</style>
