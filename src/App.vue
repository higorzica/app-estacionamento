<template>

  <Navbar :logo="logo_src" :alt="app_name" />

  <router-view /> <!--São as viwes impressas -->

  <Footer />

</template>

<script>

  import Navbar from './components/Navbar.vue';
  import Footer from './components/Footer.vue';

  export default {
    components: {
      Navbar,
      Footer
    },
    data(){
      return{
        logo_src:"/img/carro.png",
        app_name:"Cadastre o carro no Estacionamento"
      }
    }
  }

</script>

<style>
  *{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
    font-family: Arial, Arial, Helvetica, sans-serif;
  }
  .main-container{
    margin: 40px;
    min-height: 250px;;
  }
  
  h1 {
    margin-top: 10px;
    text-align: center;
    font-size: 35px;
    margin-bottom: 40px;
    color: #222;
  }
</style>
