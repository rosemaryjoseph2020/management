<template>
<div>
    <div>
      <Navigation></Navigation>
      
    </div>
       <div class="home">
     <div class="img">
       <img src="../assets/doc.jpg">
     </div>
  <section class="hero is-dark">
    <div class="hero-body">
      <div class="container">
           <h1 class="title">
          Welcome to the Med'O Clock      
        </h1>
        <div class="btn-group-vertical" >
            
            <b-button variant="outline-primary" style="margin-top:50px;"><router-link to="/AdminHospitalListing"> Hospital List</router-link></b-button>
            <b-button v-on:click="LoadMap()" variant="outline-primary" style="margin-top:50px;" >Map</b-button>
            <b-button v-on:click="LoadGraph()" variant="outline-primary" style="margin-top:50px;">Analysis</b-button>
        </div>
    
      </div>
    </div>
  </section>
</div>
     </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import axios from 'axios'
const baseURL = "http://localhost:63404/api/Home/LoadMap"
export default {
        components: {
            Navigation
        },
        methods: {
          LoadMap:function(){
            axios({
                  method: 'POST',
                  url: baseURL,
              })     
              .then(function (response) {   
                  console.log(response.data.data);
                  window.location = "http://www.google.com/maps/place/"+response.data.data.lat+","+response.data.data.long  
              })
              .catch(function (error) {    
                      console.log(error);
              });   
        },
          LoadGraph:function(){
            axios({
                  method: 'GET',
                  url: "http://localhost:63404/api/Home/LoadAnalysis",
              })     
              .then(function (response) {   
                //  console.log(response.data.data);
                  localStorage.setItem("GraphData", JSON.stringify(response.data.data));
                  console.log(localStorage.getItem("GraphData"));
                  window.location.replace('graph');
                  
              })
              .catch(function (error) {    
                      console.log(error);
              });   
        }
      }
}
</script>

<style scoped>


.img {  
    
   
    opacity:0.3;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 50px;
    width:100%;
   
  }
  .title {
    
   
    color:#0d464e;
     
   
    font: 900  arial;
    font-size: 60px;
    filter: brightness(140%);
  }
 
 
</style>