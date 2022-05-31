<template>
  <h3>Welcome from subchild</h3>
  <h5>Testing provide inject from grand parent {{username}}</h5>
</template>

<script>

export default {
    name:"subChildApp",
    inject:['username']
}
</script>

<style>

</style>