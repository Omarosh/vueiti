<template>
  <div class="form">
      <form @submit.prevent="formHandle" >
        <label for="name">Name</label>
        <input type="text" name="name" v-model="formValues.name" id="name"><br>
        <label for="age">Age</label>
        <input type="text" name="age" v-model="formValues.age" id="age"><br>
        <label for="address">Address</label>
        <input type="text" name="address" v-model="formValues.address" id="address"><br>
        <input type="radio" name="rank" v-model="rank" value="student" id="student">
        <label for="student">Student</label><br>
        <input type="radio" name="rank" value="admin" v-model="rank" id="admin">
        <label for="admin">Admin</label><br>
        <input type="submit" value="Add User">
      </form>
      {{rank}}
      {{formValues}}
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    name:"formVue",
    setup(props,context){
      
        
        const rank = ref('')
        const formValues = ref({name:"",age:"",address:""})

          function formHandle(e){
            e.preventDefault();
        if(rank.value === "student"){
            context.emit("student", formValues.value);
            // console.log("Students" , context.formValues)
        }else if(rank.value === "admin"){
            context.emit("admin", formValues.value);
            // console.log("Admin" , context.formValues)
        }
        }
        return{
            rank,formValues,formHandle
        }

    }
    ,
    // data(){
    //     return{
    //         formValues: {name:"",age:"",address:""},
    //         rank: ""

    //     }
    // },
    // methods: {
    //     formHandle(e){
    //     e.preventDefault();
    //     if(context.rank === "student"){
    //         context.$emit("student", context.formValues);
    //         console.log("Students" , context.formValues)
    //     }else if(context.rank === "admin"){
    //         context.$emit("admin", context.formValues);
    //         console.log("Admin" , context.formValues)
    //     }
        
    //     }
    // },
    // emits:['admin','student']

}
</script>

<style>

</style>