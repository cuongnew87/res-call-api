<template>
  <div>
      <img class="logo" alt="Vue logo" src="../assets/logo.png">
      <h1>Sign Up</h1>
      <div class="register">
          <input type="text" v-model="name" placeholder="Enter Name" />
          <input type="text" v-model="email" placeholder="Enter Email" />
          <input type="password" v-model="password" placeholder="Enter Password" />
          <button v-on:click="signUp">Signup</button>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data(){
        return{
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUp(){
            let result = await axios.post("https://6153335e3f4c430017159234.mockapi.io/users",{
                email: this.email,
                password: this.password,
                name: this.name
            });

            console.log(result);
            if(result.status === 201){
                alert("signup done");   
                this.$router.push({name:'Home'});
            }
        }
    },
    mounted(){
    }
}
</script>

<style>
body{
    padding: 0;
    margin: 0;
}
.logo{
    width: 100px;
}
.register input, .login input, .add input, .update input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid skyblue;
}
.register button, .login button, .add button, .update button{
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background: skyblue;
    color: #fff;
    cursor: pointer;
}
</style>