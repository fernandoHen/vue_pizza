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
    margin:0;
    padding:0;
    border:0;
}

.position-nav {
  background-color: rgb(114, 114, 114);  
  width: 100%;
  position: fixed;
  height: 100%  ;
}

</style>
