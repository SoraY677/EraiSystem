<template>
  <div>
    <PageChange></PageChange>
    <!-- <Todo
      v-for="todo in todos"
      :key="todo._id"
      :todo="todo"
      @change="changeTodo(todo._id)"
    ></Todo> -->
    <Todo checkid="hoge" backgroundcolor="backgroundcolor:#2e2e2e"></Todo>
    <TodoAdd></TodoAdd>
  </div>
</template>

<script>
import PageChange from '~/components/PageChange'
import Todo from '~/components/TodoElement'
import TodoAdd from '~/components/TodoAdd'

export default {
  components: {
    PageChange,
    Todo,
    TodoAdd
  },
  data() {
    return {
      todos: []
    }
  },
  async created() {
    await this.getTodos()
  },
  methods: {
    async getTodos() {
      const response = await this.$axios.$get(
        'https://erai-app.azurewebsites.net/api/todo',
        {
          params: {
            code: 'JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg=='
          }
        }
      )
      console.log(response)
      this.todos = response
      // this.todos = [
      //   { _id: 1, text: 'Azureでアプリを作る', isDone: false },
      //   { _id: 2, text: 'Azureでアプリを公開する', isDone: false }
      // ]
    },
    async createTodos(text) {
      await this.$axios.$post(
        'https://erai-app.azurewebsites.net/api/todo?code=JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg==',
        { text }
      )
    },
    async changeTodo(_id) {
      const todo = this.todos.find((todo) => todo._id === _id)
      console.log(todo)
      const response = await this.$axios.$put(
        'https://erai-app.azurewebsites.net/api/todo',
        { _id: todo._id, isDone: todo.isDone },
        {
          params: {
            code: 'JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg=='
          }
        }
      )
      console.log(response)
    }
  }
}
</script>
