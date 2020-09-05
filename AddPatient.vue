<template>
<div>

<div>
    <div class="row">
    <div class="col-lg-3" id="app">
        {{todos}}
        <div>
  <b-form @submit.stop.prevent>
      <label for="text-password">Patient name</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Age</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Gender</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Place</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    
    
   </b-form>
</div>
         
</div>
 <div class="col-lg-3">
     {{todos}}
      <b-form @submit.stop.prevent>
     <label for="text-password">Attacked place</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Snake type</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Status</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Time</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <label for="text-password">Date</label>
    <b-input type="text" id="text-user" aria-describedby="password-help-block"></b-input>
    <b-button variant="outline-primary" style="margin-top:20px;" href="#/patient">SUBMIT</b-button>
     </b-form>
    </div>
    </div>
    
</div>
</div>
          </template>

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
         
          </style>