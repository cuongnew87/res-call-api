<template>
  <img class="logo" src="../assets/logo.png"/>
  <h1>Login</h1>
  <div class="login">
      <input type="text" v-model="email" placeholder="Enter Email"/>
      <input type="password" v-model="password" placeholder="Enter Password"/>
      <button v-on:click="login">Login</button>
      <p>
        <router-link to="/sign-up">Signup</router-link>
      </p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'Login',
    data(){
        return{
            email:"",
            password:"",
        }
    },
    methods:{
        async login(){
            let result = await axios.get(`https://6153335e3f4c430017159234.mockapi.io/users?email=${this.email}&password=${this.password}`);

            console.log(result);
            if(result.status === 200 && result.data.length > 0){
                alert("Login susscess");   
                // localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({name:'Home'});
            }
        }
    }
}
</script>

<style>

</style>