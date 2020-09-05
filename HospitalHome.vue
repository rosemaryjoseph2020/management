<template>
    <div>
        <div>
        <Navigation></Navigation>    
        </div>
        <div class="row ">
            <div class="col-md-2">       
 <SideBarNav></SideBarNav>  
            </div>
            <div class="col-md-10 ">     
            <img src="../assets/bottle.jpg" class="" width="100%" height="550px" >     
            </div>
        </div>
    </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import SideBarNav from '@/components/SideBarNav'
export default {

    
          components: { 
                Navigation,
                SideBarNav
            },
            created(){
this.hospitalName="sample";
            }
            
}
</script>>
 <style>
  
         
</style>