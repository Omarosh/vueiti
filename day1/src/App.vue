<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
adada
  <h1>{{name}}</h1>
  <h1 v-text="name"></h1>
  <p v-html="boldname"></p>
  <p v-bind:id="myid"> BIND ID</p>
  <p v-bind:class="myclass">bindclassa</p>
  <h1>Bind CLass with condition</h1>
  <p v-bind:class="bool?class1:class2"> Bind class ternary</p>
  <button @click="bool=!bool"> toggle</button>

  <h1>Conditional Rendering</h1>
  <h3>{{num}}</h3>
  <h3 v-if="num === 0"> Num equal 0</h3>
  <h3 v-else-if="num > 0"> Num > 0</h3>
  <h3 v-else-if="num < 0"> Num &lt; 0</h3>
  <h3 v-else> Else</h3>
  <button @click="num++">++</button>
  <button @click="num--">--</button>
  <h1>Looping on array</h1>
  <div v-for="name,index in array" :key="name">
    <h3>{{index +1}} - {{name}}</h3>
  </div>
  <h1>Looping on array of objects</h1>
  <div v-for="name,index in fullnames" :key="name.fname">
    <h3>{{index +1}} - {{name.fname}} {{name.lname}} <span v-for="car in name.cars" :key="car">{{car}}-</span></h3>
  </div>
<h1>Looping on object</h1>
  <div v-for="(value,key) in myinfo" :key="key">
    <h3> {{key}} : {{value}}</h3>
   </div>
<h1>Form</h1>

{{formValues}}
<form @submit.prevent="formHandle" method="get">
  <input type="text" v-model="formValues.name" name="name" id="name">
  <br>
  <input type="text" v-model.lazy.trim="formValues.age" name="name" id="name">
  <br>
  <input type="submit" >
  
  <h1>Compute vs method</h1>
  {{compute}}
  computed methods are used for operations to be cached.
  It's better in performance as it's not called everytime the state changes

  {{method()}}


</form>

<h1> Components</h1>
<childApp/>

<h1>sending data from parent to child</h1>
<childApp name = "opensource" :fname="fname" :lname ="lname" />

<h1>Sending from child to parent</h1>
<popupApp v-if="show" @close="closePopUp" />
</template>

<script>
import childApp from './child.vue';
import popupApp from './popup.vue';
export default {
    name:"app",
    components:{
      childApp,popupApp
    },
    //provide:{username:"MY USERNAME"} ,
    provide(){return {username:this.username}} ,
    data(){
      return {
      bool:true,
      name:"omar",
      boldname: "bold",
      myid:"myid",
      myclass:"myclass",
      class1:"class1",
      class2:"class2",
      num:0,
      array:["omar","Ali","Sara"],
      fullnames:[
        {fname:"Omar",lname:"khaled", cars: ["OPEL","Tesla","PUGATTI","MBenz"]},
        {fname:"Ahmed",lname:"Ali", cars: ["OPEL","Tesla","PUGATTI","MBenz"]},
        {fname:"Ali",lname:"Mohamed" , cars: ["OPEL","Tesla","PUGATTI","MBenz"]},
        {fname:"Mohamed",lname:"Asharaf", cars: ["OPEL","Tesla","PUGATTI","MBenz"]},
      ],
      myinfo:{name:"Omar", age:24, college:"Handasa"},
      formValues : {name:"",age:""},
      fname:"Omar",
      lname:"Ali",
      username:"USername from data",
      show: true

      }
    },
    methods:{
      increase(){
        return this.num++
      },
      decrease(){
        return this.num--
      },
      formHandle(e){
        e.preventDefault();
        console.log(this.formValues)

      },
      method(){
        console.log("normal method")
      },
      closePopUp(){
        this.show = !this.show
        console.log("Hello from child event")
      }

    },
    computed :{
      compute(){
        return console.log("compyte")
      }
    },
    watch:{
      //We need to search for deep watchers and immediate watchers
      num(newValue, oldValue){
        if(newValue > oldValue && newValue > 5){
          alert("ERROR")
        }
      }
    }
  }
</script>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}
#myid{
  background-color: red;
  color: wheat;
}
.myclass{
  background-color: red;
  color: wheat;
}
.class1{
  background-color: green;
  color: wheat;
}
.class2{
  background-color: blue;
  color: wheat;
}

</style>
