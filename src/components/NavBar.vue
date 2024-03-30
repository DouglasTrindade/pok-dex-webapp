<script setup>
import { ref } from "vue";

const isDrawerOpen = ref(false);
</script>

<template>
  <v-container :fluid="true">
    <v-app-bar
      flat
      class="border-b py-2 nav-bar-shadow px-16"
      style="background-color: #f5db13"
      elevation="4"
    >
      <v-btn icon @click="isDrawerOpen = !isDrawerOpen" class="d-md-none">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
      <img class="ms-5" src="/src/assets/pokemon-logo.png" alt="Pokémon Logo" />
      <div class="d-none d-md-flex justify-end align-center w-100">
        <router-link to="/" class="nav-link mx-2 font-weight-medium"
          >Home</router-link
        >
        <router-link to="/pokedex" class="nav-link mx-2 font-weight-medium"
          >Pokédex</router-link
        >
        <router-link to="/" class="nav-link mx-2 font-weight-medium"
          >Legendaries</router-link
        >
      </div>
    </v-app-bar>

    <v-navigation-drawer
      v-model="isDrawerOpen"
      class="mt-6"
      temporary
      style="background-color: #f5db13"
    >
      <v-list>
        <v-list-item
          router
          to="/"
          prepend-icon="mdi-home"
          class="text-black font-weight-medium"
        >
          Home
        </v-list-item>
        <v-list-item
          router
          to="/pokedex"
          prepend-icon="mdi-pokeball"
          class="text-black font-weight-medium"
        >
          Pokédex
        </v-list-item>
        <v-list-item
          router
          to="/"
          prepend-icon="mdi-fencing"
          class="text-black font-weight-medium"
        >
          Legendaries
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-container>
</template>

<style scoped>
.nav-link {
  position: relative;
  color: black;
  text-decoration: none;
}

.nav-link::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 100%;
  height: 2px;
  background-color: black;
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.nav-link:hover::after {
  transform: scaleX(1);
}
</style>
