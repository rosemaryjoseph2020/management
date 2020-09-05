<template>
  <div>
    <div>
      <Navigation></Navigation>
      
    </div>
  <div>
   <div class="home">
     <div class="img">
       <img src="../assets/hos.jpg">
     </div>
  <section class="hero is-dark">
    <div class="hero-body">
      <div class="container">
        <h1 class="title">
          Welcome to the Med'O Clock      
        </h1>
        <h2 class="desc">
         
        </h2>
        <h2 class="subtitle">
          Sign Up to experience the features of our website
        </h2>
        <div class="button-block">
          <button class="button is-xl is-dark" href="#/signup">Sign Up to Browse Events</button>
        </div>
      </div>
    </div>
  </section>
</div>
 
    </div>
 </div>
</template>
<script>
import Navigation from '@/components/Navigation'
export default {
          components: {
                Navigation
            },
}
</script>>

<style scoped>
.img {  
    
   
    opacity:0.3;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 10px;
  }
  .title {
    
   
    color:#0d464e;
     padding-top:30px;
   
    font: 900  arial;
    font-size: 60px;
    filter: brightness(140%);
  }
 
  .subtitle {
    color:#0d464e;
   
    font-size: 30px;
    
    padding-bottom: 30px;
  }
  .hero is-dark{
    padding-bottom: 50px;
  }

</style>