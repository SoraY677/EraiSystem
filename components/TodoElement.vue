<template>
  <div>
    <input :id="checkid" type="checkbox" />
    <label :for="checkid">hogehoge</label>
  </div>
</template>

<script>
export default {
  props: ['checkid']
}
</script>
