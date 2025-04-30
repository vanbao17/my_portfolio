<script setup lang="ts">
import Header from "./components/layouts/Header.vue";
import Footer from "./components/layouts/Footer.vue";
import Home from "./components/pages/Home.vue";
</script>

<template>
  <div class="wrapper">
    <div class="container_wrapper">
      <Header></Header>
      <Home></Home>
      <Footer></Footer>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  background-color: var(--background-color);
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
/* .logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
} */
</style>
