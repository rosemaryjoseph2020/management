<template>
  <!-- Card -->
  <div>
      <div>
      <Navigation></Navigation>
      
    </div>
  <div class="mid" >
    <b-card header="SignUp" class="text-center">
            <b-card-text>
                <div>
                    <b-form @submit.stop.prevent>
                        <label for="text-password">Email</label>
                        <b-input type="text" id="text-user" v-model="email" name=" " aria-describedby="password-help-block"></b-input>
                        <label for="text-password">UserName</label>
                        <b-input type="text" id="text-user"  v-model="username" aria-describedby="password-help-block"></b-input>
                        <label for="text-password">Hospital Name</label>
                        <b-input type="text" id="text-password"  v-model="HospitalName" aria-describedby="password-help-block"></b-input>
                        <label for="text-password">Phone Number</label>
                        <b-input type="text" id="text-password"  v-model="PhoneNumber" aria-describedby="password-help-block"></b-input>

                        <label for="text-password">Password</label>
                        <b-input type="password" id="text-password" v-model="Password" aria-describedby="password-help-block"></b-input>
                            <label for="text-password">Confirm Password</label>
                        <b-input type="password" id="text-password" v-model="RetypePassword" aria-describedby="password-help-block"></b-input>
                        <b-button v-on:click="AddUser()" variant="outline-primary" style="margin-top:20px;">SignIn</b-button>
                    </b-form>                                                                        
                </div>
            </b-card-text>
        </b-card> 
   </div>
   </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import Navigation from '@/components/Navigation'

const baseURL = "http://localhost:63404/api/Register/AddUser"
Vue.use(VueAxios, axios)
export default {
      components: {
                Navigation
            },
      name: 'Login',
      methods: {
            AddUser: function () {
                let hassError=true;

                if(this.email==undefined)
                {
                    hassError=false;
                }
                else if(this.username==undefined){
                    hassError=false;
                }
                else if(this.HospitalName==undefined){
                    hassError=false;
                }
                else if(this.PhoneNumber==undefined){
                    hassError=false;
                }
                else if(this.Password==undefined){
                    hassError=false;
                }
                if (/@gmail\.com$/.test(this.email)) {
                if(hassError){
                    if(this.Password==this.RetypePassword){
                        const emp = {};
                        emp.FullName = this.username;
                        emp.EmailAddress = this.email;
                        emp.Passwd = this.Password;
                        emp.HospitalName = this.HospitalName;
                        emp.PhoneNumber =this.PhoneNumber;
                        axios({
                            method: 'POST',
                            url: baseURL,
                            data : emp,
                            isArray: true
                        })     
                        .then(function (response) {   
                                console.log(response);
                                if(response.data.success==true){
                                    window.location.replace('login');
                                }
                                else{
                                    alert("something error");
                                }
                        })
                        .catch(function (error) {    
                                console.log(error);
                        });

                    }
                    else{
                        alert("Your password and confirmation password do not match.");
                    }
                }
                else{
                    alert("All fields are mandatory")
                }
                }
                else{
                    alert("Enter valid Email")
                }
                

            },

    }

}
</script>>


    <style>
        .mid{
           margin-left: 300px;
           padding-left: 50px;
            width:50%;
            
        }
        </style>