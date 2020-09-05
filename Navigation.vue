<template>

  <div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-nav>
        <b-nav-item v-if="CheckAdmin==-1"><router-link to="/home">Home</router-link></b-nav-item>      
        <b-nav-item v-if="CheckAdmin==1"><router-link to="/AdminView">Home</router-link></b-nav-item>  
        <b-nav-item v-if="CheckAdmin==2"><router-link to="/HospitalHome">Home</router-link></b-nav-item>  
      </b-navbar-nav>
      <b-navbar-nav class="ml-auto">
      <b-nav-item  b-nav-item >{{hospitalName}}</b-nav-item> 
      <b-nav-item ><router-link to="/register">SignUp</router-link></b-nav-item>
      <b-nav-item v-if="!IsLogin"><router-link to="/login">Login</router-link></b-nav-item>
      <b-nav-item v-if="IsLogin"><router-link to="/login">Logout</router-link></b-nav-item>


      </b-navbar-nav>
   
  </b-navbar>
</div>
</template>

<script>
  //  import FooterComponents from '../src/components/FooterComponents';
//import nav-header from '../src/components/nav'
   export default {
     name:"navheader",
              data(){
    return{
            hospitalName:"",
            IsAdmin:localStorage.getItem("isAdmin"),
            IsLogin:(localStorage.getItem("ID")!= "null" && localStorage.getItem("ID")!= null)? true : false
    };
    },
    computed:{
      CheckAdmin:function(){
          if(this.IsAdmin !=null && this.IsAdmin !="null"){

            if(this.IsAdmin=="true"){

              return 1
            }
            else if(this.IsAdmin=="false"){

              return 2
            }
            else{return 0}
          }
          else{
            return -1
          }

      }
    }
    }
 </script>
 <style>
.navbar-dark .navbar-nav .nav-link {
    color: #f8f9fa;
}
button {
    background: #17a2b8;
    border: 1px solid #f8f9fa;
}
.nav-item a{
  color: #f8f9fa;
}
</style> 