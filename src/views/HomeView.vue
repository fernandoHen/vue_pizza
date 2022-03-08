<template>
  <div class="home main-container">
    <h2>Monte sua Pizza</h2>
    <Pizzaform />
  </div>
</template>

<script>
import Pizzaform from "../components/Pizzaform.vue";

export default {
  name: "Home",
  components: {
    Pizzaform
  }
}
</script>
