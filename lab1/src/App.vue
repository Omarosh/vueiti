<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>

  <div class="btns" style="display: inline;">
    <button @click="choice = 1">Form</button>
    <button @click="choice = 2">Show Students</button>
    <button @click="choice = 3">Admins</button>
    <div class="data" >
      <formVue  @student="addStudent" @admin="addAdmin" v-if="choice == 1" />
      <studentsVue v-if="choice == 2" :students="students" @delete="handleDeleteStudent" />
      <adminsVue v-if="choice == 3" @delete="handleDeleteAdmin" />
    </div>
  </div>
  {{students}}
  {{admins}}
</template>

<script>
import formVue from './form.vue';
import studentsVue from './students.vue';
import adminsVue from './admins.vue';
export default {
  name: "App",
  components: [formVue, studentsVue, adminsVue],
  data() {
    return {
      choice: 1,
      students: [],
      admins: []
    }
  },
  methods: {
    addStudent(std) {
      console.log("added" , this.students)
      this.students.push(std)
    },
    addAdmin(admin) {
      this.admins.push(admin)
    },
    handleDeleteStudent(index) {
      this.students.splice(index,1)
    },
    handleDeleteAdmin(index) {
      this.admins.splice(index,1)
    }
  },
  provide(){return {admins:this.admins}} 
}

</script>

<style>
.data {
  width: 300px;
  height: fit-content;
  margin-top: 20px;
  justify-content: center;

}

.data form input {
  margin-bottom: 5px;
  display: block;
}

.btns {
  width: 50%;
  height: fit-content;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;

  margin: auto;
}

.btns button {
  background-color: darkred;
  border: 2px solid yellow;
  color: yellow;
  padding: 10px;
  margin-right: 25px;
}

.btns button:hover {
  background-color: rgb(202, 13, 13);
}

.btns button:active {
  background-color: rgb(87, 2, 2);

}

body {
  background-color: crimson;
  color: white;
}
</style>
