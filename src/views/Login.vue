<template>
  <div>
    <div>
        <input placeholder="Username" type="text" v-model="username" />
        <input placeholder="Password" type="password" v-model="password" />
        <button v-on:click="login">Login</button>
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