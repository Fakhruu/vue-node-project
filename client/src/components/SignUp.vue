<template>
<div class="box" v-cloak>
<div class="register">
        <img class="logo" src="../assets/logo-stb.png"/>

    <h1>Sign Up</h1>

    <div class="type">
    <input type="text" v-model="name" placeholder="Enter Name" />
    <input type="email" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="signUp">Sign Up</button>
    <p>
        <router-link to="/Login">Login</router-link>
    </p>
    </div>
</div>

</div>

</template>

<script>

import axios from 'axios'
export default {
name: 'SignUp',
data() {
    return {
        name: '',
        email: '',
        password: '',
    }
},

methods: {
   async signUp()
    {
        // let result = await axios.post("http://localhost:3000/users", {
        //     email : this.email,
        //     password : this.password,
        //     name : this.name
        // });
        let result = {
          email : this.email,
          password : this.password,
          name : this.name
        };
      localStorage.setItem("user-info", JSON.stringify(result))
         this.$router.push({name:'Home'})
    //  console.warn(result);
    //  if (result.status==201)
    //  {
    //     //  alert("sign up done");
    //      localStorage.setItem("user-info", JSON.stringify(result.data))
    //      this.$router.push({name:'Home'})
    //  }
    }
},

    mounted()
    {
        let user = localStorage.getItem('user-info');

        if(user)
        {
            this.$router.push({name:'Home'})
        }
    }
}
</script>

<style>

</style>
