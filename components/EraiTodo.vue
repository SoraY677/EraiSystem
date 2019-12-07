<template>
  <div>
    <div>{{ todo.text }}</div>
    <b-btn @click="$emit('click')">{{ todo.erai }}えらい！</b-btn>
  </div>
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
  }
}
</script>
