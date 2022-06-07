<template>
<div>
<div>  {{students}}</div>

  <h1>Students</h1>
  
  <table>
  <tr>
    <th>index</th>
    <th>Name</th>
    <th>Age</th>
    <th>Address</th>
    <th>Action</th>
  </tr>
  <tr v-for="std,index in students" :key="std.name">
    <td >{{index}}</td>
    <td >{{std.name}}</td>
    <td >{{std.age}}</td>
    <td >{{std.address}}</td>
    <td ><button @click="$emit('delete',index)">Delete</button></td>
  </tr>

</table>
</div>
</template>

<script>
export default {
    name: "studentsVue",
     props:['students'],
    
    
}
</script>

<style>
table, th, td {
  border: 1px solid;
  width: 100%;
  padding: 5px;
}
</style>