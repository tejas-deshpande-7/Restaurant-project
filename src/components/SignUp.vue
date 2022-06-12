<template>
<img class="logo" alt="resto-logo" src="../assets/resto-logo.jpg"/>
  <h3>Sign Up</h3>
  <div class="register" id="SignUpFrm">
    <input type="text" v-model="name" placeholder="Enter Name"/>
    <input type="text" v-model="email" placeholder="Enter Email"/>
    <input type="password" v-model="password" placeholder="Enter Password"/>
    <button v-on:click="signUp">Sign Up</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'SignUp',
    data(){
      return{
        name:'',
        email:'',
        password:''
      }
    },
    methods:{
      async signUp()
      {
        console.warn("The SignUp Method is called !",this.name,this.email,this.password)
        let result = await axios.post("http://localhost:3000/users",{
          name:this.name,
          email:this.email,
          password:this.password
        })
        console.warn(result)
        if(result.status == 201)
        {
          alert("SignUp Completed !");
        }
        localStorage.setItem("user-info",JSON.stringify(result.data))
        document.getElementsById('SignUpFrm')[0].reset()
        
      }
    }
}
</script>

<style>
.logo{
    width:250px;
    height: 150px;
}
h3{
   font-weight: bolder;
    size: 250px;
    font-style: oblique;
    font-family: cursive;
    color: blue;
    text-decoration: underline;
}
.register input{
  width: 300px;
    height: 30px;
    display: block;
    margin-bottom: 20px;
    margin-left: auto;
    margin-right: auto;
    border:1px solid brown;
}
.register button{
  width:280px;
  height:40px;
  border:1px solid red;
  background-color: coral;
  color:white;
}
</style>