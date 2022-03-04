<template>
  <Navbar />
  <router-view/> <!--a view é mostrada nesse momento-->
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
  }
}
</script>



<style>


</style>
