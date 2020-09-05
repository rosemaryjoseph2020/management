<template>
    <div >
        <div class="row">
            <div class="">
                <div class="side">
                    <ul class="social">
                    <li>
                        <ul >
                            <li><a  class="icons-sm fb-ic"><router-link to="/Patient">Add Patient Details</router-link></a></li>
                            <li><a  class="icons-sm pin-ic"><router-link to="/stock"> Stock</router-link></a></li>
                            <li><a class="icons-sm gplus-ic"><router-link to="/PatientList"> Patient List</router-link></a></li>
                            <li><a class="icons-sm gplus-ic"><router-link to="/VialCountList"> Stock List</router-link></a></li>
                            <!-- <li><a href="#" @click="Login()" class="icons-sm tw-ic">Logout</a></li> -->
                        </ul>
                    </li>
                    </ul>        
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    method:{
        logout:function(){
            localStorage.setItem("isAdmin", null);
            localStorage.setItem("ID", null);
        }
    }
}
</script>>


 <style>
    .side{
    background-color: #aadae9;
    height:550px;
    width:300px;
    }
    li{
        font-size: 0.5cm;
        padding-bottom: 10px;
        font-family:'Times New Roman', Times, serif;
        color: #17a2b8;
        text-align: left;
    }
    .social{
        list-style: none;
    }
         
</style>
