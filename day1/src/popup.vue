<template>
<h1> popup</h1>
  <div>
      <input type="text" v-model="name">
      <button @click="$emit('close' , name)">toggle</button>
  </div>
</template>

<script>

export default {
    name:"popupApp",
    emits:['close']
}
</script>

<style>

</style>