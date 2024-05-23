<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <RouterView />
  <Footer />
</template>

<script>
export default {
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Ur Burger"
    }
  }
}
</script>
