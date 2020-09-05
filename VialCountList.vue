<template>
  <div>
          <div>
      <Navigation></Navigation>
      
    </div>
            <div class="row">
                <div class="col-lg-3">
                    
 <SideBarNav></SideBarNav> 
                    
                </div>
  <div class="col-lg-9 padleft">
        <b-table   b-table striped hover :items="items" :fields="fields"></b-table>
    </div>
                </div>

  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import SideBarNav from '@/components/SideBarNav'
import axios from 'axios'
  export default {
            components: {
                Navigation,
                SideBarNav
            },
    data() {
      return {
        // Note 'isActive' is left out and will not appear in the rendered table
        fields: [
          {
            key: 'hospitalName',
            sortable: true
          },
          {
            key: 'stockCount',
            sortable: false
          }
        ],
        items: [],
      }
    },
        async created(){
        try{
            const res=await axios.post("http://localhost:63404/api/Home/StockList/"+parseInt(localStorage.getItem("ID")))
            this.items=res.data.data;
            console.log(res)
        }
        catch(e){
            console.error(e);
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
          .padleft{
              padding: 0%;
              margin-left: -25px;

          }
         
          </style>