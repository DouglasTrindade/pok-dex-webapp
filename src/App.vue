<script setup>
import Footer from "./components/Footer.vue";
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
