<template>

<div id="app1">

      <Navigation></Navigation>

    <div class="row">

    <div class="col-lg-3">
        <div class="side">
        <ul >
          <li>
            <ul class="social">
            <li><a href="#/patient" class="icons-sm fb-ic">Patient Details</a></li>
            <li><a href="#/stock" class="icons-sm pin-ic">Stock</a></li>
            <li><a href="#" class="icons-sm gplus-ic">List</a></li>
            <li><a href="#/login" class="icons-sm tw-ic">Logout</a></li>
            </ul>
          </li>
          </ul>
          
   <div id="mess" class="">{{ selectedFruit }}</div>
                           <input
                          class="form-control inpt_style"
                          type="text"
                          placeholder="Mobile"
                          required
                          v-model="selectedFruit"
                          maxlength="11"
                        />
        </div>
    </div>
    <div class="col-lg-9">
            <AddPatient></AddPatient>
            </div>
</div>
</div>
</template>
<script>
import Vue from 'vue';
import Vuex from 'vuex';

// Global state management


import Navigation from '@/components/Navigation'
import AddPatient from '@/components/AddPatient'
import axios from 'axios'
import VueAxios from 'vue-axios'
const baseURL = "http://localhost:63404/api/Home/LoadLocation"
export default {
name:"app",
data(){
  return{
    todos:[]
  };
},
    components: {
        AddPatient,
        Navigation
    },   
async created(){
  try{
    const res=await axios.post(baseURL)
    this.todos=res.data.data;
    console
  }
  catch(e){
    console.error(e);
  }
  
},

}
</script>

 <style>
    .side{
    background-color: #aadae9;
    height:1000px;
    width:300px;
    }
    li{
        font-size: 0.5cm;
        padding-bottom: 10px;
        font-family:'Times New Roman', Times, serif;
        color: #17a2b8;
    }
         
</style>
