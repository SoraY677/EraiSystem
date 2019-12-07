<template>
  <div>
    <PageChange></PageChange>
    <Todo checkid="hoge"></Todo>
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
  methods: {
    async getTodos() {
      await this.$axios.$get(
        'https://erai-app.azurewebsites.net/api/todo?code=JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg=='
      )
    },
    async createTodos(text) {
      await this.$axios.$post(
        'https://erai-app.azurewebsites.net/api/todo?code=JrXk2jWlKTFOaBigeJRbYApgmK//Zqz2TRTPzjHbZDKLTbzjUx88Sg==',
        { text }
      )
    }
  }
}
</script>
