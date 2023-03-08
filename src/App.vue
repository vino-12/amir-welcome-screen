<template>
  <div class="container">
    <div class="row">
      <div class="col text-center" style="font-size:50px;font-weight:bold;">
    
      </div>
    </div>
  </div>

 
    <div class="container">
      <ul>   
        <li>
          <span class=""><WelcomeToOpportunity msg="Welcome to Opportunity"/></span>
        </li>
      </ul>
      
        <event-component></event-component>
    </div>
<!-- logo footer -->
  <footer>
    <div class="footer-wrapper">
      <div class="footer-item">
        <img src="./assets/STZH_SEB_Logo.png" alt="Image 1">
      </div>
      <div class="footer-item">
        <img src="./assets/Opportunity.png" alt="Image 2">
      </div>
      <div class="footer-item">
        <img src="./assets/SAG_Logo_De.png" alt="Image 3">
      </div>
    </div>
  </footer>

</template>

<script>
/* import HelloWorld from './components/HelloWorld.vue' */
import WelcomeToOpportunity from './components//WelcomeToOpportunity.vue'
import EventComponent from './components/EventComponent.vue';
/* import EventFilter from "@/components/EventFilter.vue"; */
export default {
  name: 'App',
  components: {
    /* HelloWorld, */
    WelcomeToOpportunity,
    EventComponent,
    /* EventFilter, */
  }
 
}
</script>

<style>
#app {
  font-family: "Inter", Helvetica, Arial, sans-serif;
  /* font-family: 'Inter', sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body {
  background-color: #E8EFF4;
  margin-bottom:25vh;
}
/* .infoBoxBs {
  background-color: #0F05A0;
  padding-left:25px;
} */
footer {
  background-color:white;
  padding: 20px;
  position:fixed;
  bottom: 0;
  z-index: 1;
}
.footer-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 100%;
  margin: 0 auto;
}
.footer-item {
  flex-basis: calc(33.33% - 10px);
  text-align: center;
}
.footer-item img {
  max-width: 100%;
 
}
ul {
  list-style: none;
}
</style>