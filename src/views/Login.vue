<template>
  <div class="loginBackground">
    <div class="content">
        <div class="logo">
          <img src="../assets/icons/apartner_logo1_white.png"><br>
         <img src="../assets/icons/apartner_logo2_white.png">
        </div>
        
        <input placeholder="Username" type="text" v-model="username" />
        <input placeholder="Password" type="password" v-model="password" /><br>
        <button v-on:click="login">Login</button>
        <p class="signup">
          <router-link to="/signup" class="loginlink">Forgot password?</router-link>
          |
          <router-link to="/signup" class="loginlink">Create Account</router-link>
        </p>
    </div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    login: function() {
      this.$http
        .post("localhost:3000", {
          username: this.username,
          password: this.password
        })
        .then(function(data) {
            if (data.valid==true){
                this.$router.go("/home");
            }else{
                alert("Invalid account or password");
            }
            
        });
    }
  }
};
</script>

<style scoped>
.content{
  margin: auto;
    margin-top:20%;
    margin-bottom: 20%;
    overflow: hidden;
    /* position: relative; */
    /* width: 80%; */
    text-align: center;
    display: inline-block;
}
.loginBackground{
  background: url('../assets/backgrounds/login.jpg') center /cover;
  height:100%;
  width:100%;
  overflow:hidden;
}
input,select{
    border: 1px solid #fff;
    background: transparent;
    border-radius: 20px;
    font-size: 12px;
    height: 35px;
    padding: 6px 15px;
    margin: 10px;
    color:#fff;
    width: 200px;
  }
  input:focus {
    color: #fff;
  }
  ::placeholder { 
  color: #ffffff;
  opacity: 1;
  }

button{
  border: 0px ;
    background: rgb(41,171,97);
    border-radius: 20px;
    font-size: 12px;
    height: 35px;
    padding: 6px 15px;
    margin: 10px;
    color:#fff;
    width: 200px;
}
.logo{
  width:40%;
  margin: 10%;
  text-align: center;
  display: inline-block;
}
.signup{
  color:#fff;
  text-decoration: none;
  font-size: 11px;
}
.loginlink{
  color:#fff;
  text-decoration: none;
  font-size: 11px;
  margin: 10px;
}
</style>