
<template>
  <div id="app">
    {{todos}}
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
async created(){
  try{
    const res=await axios.post(`http://localhost:63404/api/Home/LoadLocation`)
    this.todos=res.data.data;
    console
  }
  catch(e){
    console.error(e);
  }
  
},
//  mounted() {
//         axios({
//             method: 'POST',
//             url: baseURL,
//             isArray: true
//         })     
//         .then(function (response) {   
//                 console.log(response.data.data[0].locationName);
//                 if(response.data.success==true){

//                 //commit('updateData', response.data);
//                 this.todos=response.data.data;
//                     //  self.datas=response.data.data;
//                     // this.selectedFruit=response.data.data[0].locationName;
//                     // console.log(self.selectedFruit);
//                     // if(response.data.data.isAdmin==true){
//                     //     window.location.replace('adminview');
//                     // }
//                     // else{
//                     //     window.location.replace('hospitalHome');
//                     // }
//                 }
//                 else{
//                     alert("Enter Valid username and password");
//                 }
//                 // window.location.replace('login');
//         })
//         .catch(function (error) {    
//                 console.log(error);
//         });  
// }
}
</script>

<style>

</style>