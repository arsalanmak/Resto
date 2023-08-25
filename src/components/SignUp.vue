<template>
  <img class="logo" src="../assets/Rest-logo.jpg" alt="">
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" v-model="name" placeholder="Enter your name">
    <input type="email" v-model="email" placeholder="Enter your email">
    <input type="password" v-model="password" placeholder="Enter your password">
    <button v-on:click="signUp">Sign Up</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name : 'SignUp',
  data(){
    return{
      name: '',
      email: '',
      password: ''
    }
  },
  methods:{
    async signUp(){
      // console.warn("Sign Up", this.name, this.email, this.password);
      let result = await axios.post("http://localhost:3000/user",{
        email: this.email,
        name: this.name,
        password: this.password
      });
      console.log(result);

      if(result.status == 201){
        alert("Signed Up Done");
        localStorage.setItem("user-info", JSON.stringify(result.data))
      }
    }
  }
}
</script>

<style>
.logo{
  width: 150px;
}
.register input{
  display: block;
  width: 300px;
  height: 40px;
  padding-left: 8px;
  margin-bottom: 20px;
  margin-left: auto;
  margin-right: auto;
  border: 2px solid skyblue;
  border-radius: 5px;
}
.register button{
  background-color: black;
  color: white;
  padding: 10px 25px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>