<template>
<div>
    <div v-if="IsLogin">
     <div>
      <Navigation></Navigation> 
    </div>
    <div class="container-fluid">
    <div class="row">
 <SideBarNav></SideBarNav>
    <div class="col-lg-3 lblLeft">
          <div >
                <div>
                    <b-form @submit.stop.prevent>
                            <label for="text-password">Patient name</label>
                            <b-input type="text" id="text-user" v-model="name" aria-describedby="password-help-block"></b-input>
                            <label for="text-password">Age</label>
                            <b-input type="text" id="text-user" v-model="age"  aria-describedby="password-help-block"></b-input>
                            <label for="text-password">Gender</label>
                            <b-input type="text" id="text-user" v-model="gender"  aria-describedby="password-help-block"></b-input>
                            <label for="text-password">Place</label>
                            <b-input type="text" id="text-user" v-model="place" aria-describedby="password-help-block"></b-input>   
                    </b-form>
                </div>         
            </div>
           
    </div>
     <div class="col-lg-3">
                <b-form @submit.stop.prevent>

                        <label for="text-password">Attacked place</label>
                        <div>
                            <b-form-select v-model="selected" :options="todos"></b-form-select>
                            <!-- <div class="mt-3">Selected: <strong>{{ selected }}</strong></div> -->
                        </div>

                        <label for="text-password">Status</label>
                        <div>
                            <b-form-select v-model="ddlStatus" :options="ddlStatusList"></b-form-select>
                            <!-- <div class="mt-3">Selected: <strong>{{ selected }}</strong></div> -->
                        </div>

                        <label for="text-password">Snake type</label>
                        <b-input type="text" id="text-user" v-model="snakeType" aria-describedby="password-help-block"></b-input>
                        <!-- <label for="text-password">Status</label>
                        <b-input type="text" id="text-user" v-model="status" aria-describedby="password-help-block"></b-input> -->
                        <label for="text-password">Time</label>
                        <b-form-timepicker v-model="Time" locale="en"></b-form-timepicker>
                        
                </b-form>
            </div>

                 <div class="col-lg-3">
                <b-form @submit.stop.prevent>
                        <label for="text-password">Date</label>
                        <b-form-datepicker id="example-datepicker" v-model="date" class="mb-2"></b-form-datepicker>
                </b-form>
                <label for="text-password">Count</label>
                <b-input type="text" id="text-user" v-model="count"  aria-describedby="password-help-block"></b-input>
                            
            </div>
            <div class="col-lg-12 btnSubmit">
<b-button v-on:click="AddPatient()" variant="outline-primary" style="" >SUBMIT</b-button>
            </div>
                                        
</div>
 
    </div>

    </div>
        <div v-else>
             <Home></Home> 
    </div>
    </div>
</template>

<script>

// Global state management


import Navigation from '@/components/Navigation'
import Home from '@/components/Home'
import SideBarNav from '@/components/SideBarNav'
import axios from 'axios'
const baseURL = "http://localhost:63404/api/Home/AddPatient"
export default {
    name:"app",
    data(){
    return{
        selected: null,
        IsLogin:localStorage.getItem("ID")!= "null" ? true : false,
        Time:'',
        date:'',
        todos:[],
        ddlStatus: null,
        ddlStatusList: [
          { value: null, text: 'Please select an option' },
          { value: '0', text: 'Alive' },
          { value: '1', text: 'Death' },
        ]
    };
    },
    components: {
        Navigation,
        SideBarNav,
        Home
    },   
    async created(){
        try{
            const res=await axios.post("http://localhost:63404/api/Home/LoadLocation")
            this.todos=res.data.data;
            console
        }
        catch(e){
            console.error(e);
        } 
    },
     methods: {
            AddPatient: function () {
                let hassError=true;
                let hassErrorNumber=true;

                if(this.name==undefined)
                {
                    hassError=false;
                }
                else if(this.age==undefined){
                    hassError=false;
                }
                else if(this.gender==undefined){
                    hassError=false;
                }
                else if(this.place==undefined){
                    hassError=false;
                }
                else if(this.snakeType==undefined){
                    hassError=false;
                }                
                else if(this.Time==undefined){
                    hassError=false;
                }
                else if(this.date==undefined){
                    hassError=false;
                }
                else if(this.count==undefined){
                    hassError=false;
                }
                if(hassError){
                    if(Number.isInteger(parseInt(this.age))&& parseInt(this.age)>0)
                    {
                        hassErrorNumber=true;
                    }
                    else{
                        hassErrorNumber=false;
                        alert("Enter valid age");
                    }
                    if(Number.isInteger(parseInt(this.count)) && parseInt(this.count)>=0 )
                    {
                        hassErrorNumber=true;
                    }
                    else{
                        hassErrorNumber=false;
                        alert("Enter valid count");
                    }
                }
                else{
                    alert("All fields are mandatory")
                }
                if(hassErrorNumber){
                    if(this.Password==this.RetypePassword){
                        const patient = {};
                        patient.PatientName = this.name;
                        patient.Age = parseInt(this.age);
                        patient.Gender = this.gender;
                        patient.Place = this.place;
                        patient.AttackedPlaceID =parseInt(this.selected);
                        patient.Count =parseInt(this.count);
                        patient.Status =this.ddlStatus == "0" ? false : true;
                        patient.Time =this.Time;
                        patient.Date =this.date;
                        patient.HospitalID =parseInt(localStorage.getItem("ID"));
                        console.log(patient);
                        axios({ 
                            method: 'POST',
                            url: baseURL,
                            data : patient,
                            isArray: true
                        })     
                        .then(function (response) {   
                                console.log(response);
                                if(response.data.success==true){
                                   alert("sucess");
                                }
                                else{
                                    alert("Vial count Unavilable");
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

                

            }
     }


}
</script>
          <style>
          .side{
           background-color: #aadae9;
           height:600px;
           width:300px;
          }
          li{
              font-size: 0.5cm;
              padding-bottom: 10px;
              font-family:'Times New Roman', Times, serif;
              color: #17a2b8;
          }
          .btnSubmit{
              margin-top: -250px;
              text-align: center;
              margin-left: 100px;
              position: relative;
          }
          .lblLeft{
              margin-left: 20px;
          }
         
          </style>