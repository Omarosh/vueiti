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
export default {
    name:"formVue",
    data(){
        return{
            formValues: {name:"",age:"",address:""},
            rank: ""

        }
    },
    methods: {
        formHandle(e){
        e.preventDefault();
        if(this.rank === "student"){
            this.$emit("student", this.formValues);
            console.log("Students" , this.formValues)
        }else if(this.rank === "admin"){
            this.$emit("admin", this.formValues);
            console.log("Admin" , this.formValues)
        }
        
        }
    },
    emits:['admin','student']

}
</script>

<style>

</style>