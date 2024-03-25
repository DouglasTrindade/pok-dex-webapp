<template>
  <v-container>
    <v-responsive>
      <v-app-bar
        flat
        class="border-b py-2 nav-bar-shadow"
        style="background-color: #f5db13"
        elevation="4"
      >
        <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen">
        </v-app-bar-nav-icon>
        <v-app-bar-title>
          <img src="/src/assets/pokemon-logo.png" alt="Pokémon Logo" />
        </v-app-bar-title>
      </v-app-bar>

      <v-navigation-drawer v-model="isDrawerOpen" temporary>
        <v-list>
          <v-list-subheader>Menu</v-list-subheader>
          <v-list-item prepend-icon="mdi-home">Home</v-list-item>
          <v-list-item prepend-icon="mdi-pokeball">Pokédex</v-list-item>
          <v-list-item prepend-icon="mdi-fencing">Legendaries</v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-responsive>
  </v-container>
</template>

<script setup>
import { ref } from "vue";

const isDrawerOpen = ref(false);
</script>

<style scoped></style>
