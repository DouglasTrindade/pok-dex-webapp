<template>
  <v-app>
    <v-main>
      <router-view />
      <Home />
    </v-main>

    <Footer />
  </v-app>
</template>

<script>
import Footer from "./components/Footer.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {
    Footer,
  },
});
</script>

<style>
/* global styles */
</style>
