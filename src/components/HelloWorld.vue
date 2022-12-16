<template>
  <v-container>
    <v-text-field
    v-model="email"
    />
    <v-text-field
    v-model="password"
    />
    <v-btn
    @click="login">
    Log in
    </v-btn>



    <v-btn
    @click="apiCall"
    >Test API</v-btn>
  </v-container>
</template>

<script>
import axios from 'axios';
  export default {
    name: 'HelloWorld',

    data() {
        return {
            apiKey : process.env.VUE_APP_API_KEY,
            apiUrl : process.env.VUE_APP_API_URL,
            email : "",
            password : ""
        }
    },
    methods: {
        apiCall() {
            // Axios call
            console.log(this.apiKey);
            console.log(this.apiUrl+"client");
            console.log(this.username);
        },
        login(){
            axios.request({
                method : "POST",
                url : "https://reqres.in/api/login",
                data : {
                    email : this.email,
                    password : this.password
                }
            }).then((response)=>{
                console.log(response);
            }).catch(()=>{
                console.log("error");
            })
        }
    },
  }
</script>
