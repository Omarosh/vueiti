<template>
  <h3>Welcome from child</h3>
  <h4>Testing static props from parent: {{name}}</h4>
  <h4>Testing dynamic props from parent {{fname}} {{lname}} </h4>
  
  <subchildApp/>
</template>

<script>
import subchildApp from './subchild.vue'
export default {
    name:"childApp",
    props: ['name', 'fname' , 'lname'],
    components:{
        subchildApp
    }
}
</script>

<style>

</style>