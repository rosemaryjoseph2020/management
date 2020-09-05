<template>
<div>
    <div>
      <Navigation></Navigation>
      
    </div>
 <div class="mid">
   <div class="container">
    <b-card header="LOGIN" class="text-center">
            <b-card-text>
                <div>
                    <b-form @submit.stop.prevent>
                        <label for="text-password">Username</label>
                        <b-input type="text" id="text-user" aria-describedby="password-help-block" v-model="username" name="username" class="form-control" ></b-input>
                        <label for="text-password">Password</label>
                        <b-input type="password" id="text-password" aria-describedby="password-help-block" v-model="password" name="password" class="form-control"></b-input>
                        <!-- <b-form-text id="password-help-block">
                        Your password must be 8-20 characters long, contain letters and numbers, and must not
                        contain spaces, special characters, or emoji.
                        </b-form-text> -->
                        <b-button v-on:click="Login()" variant="outline-primary" style="margin-top:20px;" href="#/dash">Login</b-button>
                    </b-form>
                </div>
            </b-card-text>
        </b-card>
   </div>
 </div>
 </div>
</template>
<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import Navigation from '@/components/Navigation'

const baseURL = "http://localhost:63404/api/login/SignUp"
Vue.use(VueAxios, axios)
export default {
      components: {
                Navigation
            },
      name: 'Login',
      methods: {
            Login: function () {
               //  window.location = "http://www.google.com/maps/place/49.46800006494457,17.11514008755796"
                let hassError=true;
                if(this.username==undefined)
                {
                    hassError=false;
                }
                else if(this.password==undefined){
                    hassError=false;
                }
                if(hassError){
                    const emp = {};
                    emp.EmailAddress = this.username;
                    emp.Passwd = this.password;
                    axios({
                        method: 'POST',
                        url: baseURL,
                        data : emp,
                        isArray: true
                    })     
                    .then(function (response) {   
                        
                            console.log(response.data);
                            if(response.data.success==true){
                                if(response.data.data.isAdmin==true){
                                    localStorage.setItem("isAdmin", true);
                                    localStorage.setItem("ID", response.data.data.id);
                                    window.location.replace('adminview');
                                }
                                else{
                                    localStorage.setItem("isAdmin", false);
                                    window.location.replace('hospitalHome');
                                    localStorage.setItem("ID", response.data.data.id);
                                }
                            }
                            else{
                                alert("Enter Valid username and password");
                                localStorage.setItem("ID", null);
                            }
                           // window.location.replace('login');
                    })
                    .catch(function (error) {    
                            console.log(error);
                    });  
                }
                else{

                    alert("All fields are mandatory");
                }
                
               
     },
     Validate:function(){
         let hassError=true;
         if(this.username=="")
         {
             hassError=false;
         }
         else if(this.password==""){
             hassError=false;
         }
         return hassError;
     }

    },
    created(){
        localStorage.setItem("isAdmin", null);
        localStorage.setItem("ID", null);
    }

}
</script>>
    <style>
        .mid{
           margin-left: 300px;
           padding-left: 50px;
            width:50%;
            
            
        }
        .container{
          padding-top: 70px;
        }
        </style>