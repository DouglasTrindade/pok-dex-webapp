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

<template>
  <v-app>
    <v-main style="background-color: #f5db13">
      <router-view />
    </v-main>

    <Footer />
  </v-app>
</template>

<style>
/* global styles */
</style>
