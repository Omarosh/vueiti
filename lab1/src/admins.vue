<template>
  <h1>Admins</h1>
  <table>
   <tr>
    <th>index</th>
    <th>Name</th>
    <th>Age</th>
    <th>Address</th>
    <th>Action</th>
  </tr>
  <tr v-for="admin,index in admins" :key="admin.name">
    <td >{{index}}</td>
    <td >{{admin.name}}</td>
    <td >{{admin.age}}</td>
    <td >{{admin.address}}</td>
    <td ><button @click="$emit('delete',index)">Delete</button></td>
    
  </tr>

</table>
</template>

<script>
export default {
    name: "adminsVue",
    inject:['admins']
}
</script>

<style>

</style>