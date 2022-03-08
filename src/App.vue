<template>
    <div class="position-nav">
      <Navbar :vueLogo="logo_src" :vueAlt="app_name" />
      <router-view/> <!--a view é mostrada nesse momento-->
    </div>
    <Footer />
</template>

<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'AppPrincipal',
  components: {
    Navbar,
    Footer
  },
  //data() - passa os dados de forma dinamica, atravez de seus :props
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Faça Seu Pedido Top"
    }
  }
}
</script>

<style>
  *{
    font-family: Helvetica;
    margin:0;
    padding:0;
    border:0;
    box-sizing: border-box; /*div nao passa da argura maxima da div pai*/
  }

  .position-nav {
    background-color: rgb(114, 114, 114);  
    width: 100%;
    position: fixed;
    height: 100%;
    display: inline-flex;
  }

  .main-container {
    margin: 0px 0px 0px px;
    min-height: 250px;
    width: 100%;
    background-color: grey;
    overflow-y: auto;
    min-width: 20px;
  }

  .main-container h2 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }

</style>
