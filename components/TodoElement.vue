<template>
  <div class="todo-element" :style="backgroundcolor">
    <input :id="checkid" type="checkbox" />
    <label :for="checkid">
      <p>hogehoge</p>
      <img src="~/assets/images/erai.png" />
      <p>200</p>
    </label>
  </div>
</template>

<script>
export default {
  props: ['checkid', 'backgroundcolor']
}
</script>

<style>
.todo-element {
  height: 60px;
  text-align: center;
  width: 80%;
  margin: auto;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
  margin: 10px auto 10px auto;
  border-radius: 2%;
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.4);
}
label {
  height: 100%;
  width: 80%;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
}

p {
  float: left;
  font-size: 20px;
  margin: 0 15px 0 15px;
}

input {
  float: left;
}

img {
  height: 60%;
  float: left;
}
</style>
