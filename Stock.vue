<template>
  <div>
      <Navigation></Navigation>

     
<div class="row">
    <div class="col-lg-3">
 <SideBarNav></SideBarNav>
    </div>
    <div class="col-lg-4 lblLeft">
        <b-form @submit.stop.prevent>
            <!-- <label for="text-password">stock id</label>
            <b-input type="text" id="text-user"  aria-describedby="password-help-block"></b-input> -->
            <label for="text-password">Batch No</label>
            <b-input type="text" id="text-user" v-model="batchNo" aria-describedby="password-help-block"></b-input>
            <label for="text-password">number of vial</label>
            <b-input type="text" id="text-user" v-model="numberOfVial" aria-describedby="password-help-block"></b-input>
            <label for="example-datepicker">Choose a date</label>
            <b-form-datepicker id="example-datepicker" v-model="ExpireyDate" class="mb-2"></b-form-datepicker>
            <b-button v-on:click="AddStock()"  variant="outline-primary" style="margin-top:20px;" >SUBMIT</b-button>
        </b-form>
    </div>
</div>

    </div>

</template>

<script>


// Global state management


import Navigation from '@/components/Navigation'
import SideBarNav from '@/components/SideBarNav'
import axios from 'axios'
const stockURL = "http://localhost:63404/api/Home/AddStock"
export default {
    name:"app",
    data(){
    return{
        selected: null,
        ExpireyDate:''
    };
    },
    components: {
        Navigation,
        SideBarNav
    },   
     methods: {
            AddStock: function () {
                let hassError=true;
                let hassErrorNumber=true;

                if(this.batchNo==undefined)
                {
                    hassError=false;
                }
                else if(this.numberOfVial==undefined){
                    hassError=false;
                }
                else if(this.ExpireyDate==undefined){
                    hassError=false;
                }
                
                if(hassError){
                    if(Number.isInteger(parseInt(this.numberOfVial)))
                    {
                        hassErrorNumber=true;
                    }
                    else{
                        hassErrorNumber=false;
                        alert("Enter valid Number");
                    }
                }
                else{
                    alert("All fields are mandatory")
                }
                if(hassErrorNumber){
                    if(this.Password==this.RetypePassword){
                        const stock = {};
                        stock.BatchNumber = this.batchNo;
                        stock.Count = parseInt(this.numberOfVial);
                        stock.ExpireyDate = this.ExpireyDate;
                        stock.HospitalID = parseInt(localStorage.getItem("ID"));
                        console.log(stock);
                        axios({ 
                            method: 'POST',
                            url: stockURL,
                            data : stock,
                            isArray: true
                        })     
                        .then(function (response) {   
                                console.log(response);
                                if(response.data.success==true){
                                   alert("sucess");
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

                

            }
     }


}
</script>

<style>
.lblLeft{
    text-align: left;
}
</style>