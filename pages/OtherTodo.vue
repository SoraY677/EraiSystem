<template>
  <div>
    <PageChange></PageChange>
    <EraiTodo
      v-for="todo in todos"
      :key="todo._id"
      :todo="todo"
      @click="sendErai(todo._id)"
    ></EraiTodo>
  </div>
</template>
<script>
import PageChange from '~/components/PageChange'
import EraiTodo from '~/components/EraiTodo'

export default {
  components: {
    PageChange,
    EraiTodo
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
      this.todos = response
      // this.todos = [
      //   { _id: 1, text: 'Azureでアプリを作る', isDone: false },
      //   { _id: 2, text: 'Azureでアプリを公開する', isDone: false }
      // ]
    },
    async sendErai(_id) {
      const todo = this.todos.find((todo) => todo._id === _id)
      const response = await this.$axios.$put(
        'https://erai-app.azurewebsites.net/api/todo',
        { _id: todo._id, erai: todo.erai + 1 },
        {
          params: {
            code: 'JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg=='
          }
        }
      )
      this.todos = response
    }
  }
}
</script>
