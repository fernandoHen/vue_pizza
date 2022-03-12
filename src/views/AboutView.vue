<template>
  <div class="main-container">
    <h2>SOBRE</h2>
    <h4>Para mais informações, entre em contato:</h4>
    <div class="about">
      <div class="linkedin">
          <a href="https://www.linkedin.com/in/fernando-henrique-seefeldt-cossa-206163108" title="Meu Linkedin" target="_blank"><img src="img/linkedin.png" alt="Meu Linkedin" ></a>
      </div>  
      <div class="github">
          <a href="https://github.com/fernandoHen" title="Meu GitHub" target="_blank"><img src="img/github.png" alt="Meu Linkedin"></a>
      </div> 
    </div>
  </div>
</template>

<script>
export default {
    name: 'navbar',
    props: ['vueLogo', 'vueAlt']
}
</script>

<style scoped>
    .about {
      height: 400px;
      width: 700px;
      margin: 0px auto;
      padding: 50px;
      display: flex;
    }

    img {
      width: 250px;
    }

    img:hover {
      opacity: 0.5;
    }

    .linkedin,
    .github {
      margin: 0px auto;
    }
</style>


