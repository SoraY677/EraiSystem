<template>
  <b-card :class="cardClass">
    <b-card-text>{{ todo.text }}</b-card-text>
    <b-btn @click="$emit('click')" variant="primary"
      >{{ todo.erai }}えらい！</b-btn
    >
  </b-card>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  computed: {
    cardClass() {
      if (this.todo.erai >= 100) {
        return ['m-4', 'col3']
      } else if (this.todo.erai >= 50) {
        return ['m-4', 'col2']
      } else if (this.todo.erai >= 10) {
        return ['m-4', 'col1']
      } else {
        return ['m-4']
      }
    }
  }
}
</script>
<style>
.col3 {
  background: orangered;
}
.col2 {
  background: pink;
}
.col1 {
  background: lightblue;
}
</style>
