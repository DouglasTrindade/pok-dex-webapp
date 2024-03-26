<script setup>
import NavBar from "@/components/NavBar.vue";
</script>

<template>
  <v-main class="home-container">
    <v-container>
      <NavBar />

      <v-row no-gutters>
        <v-col cols="12" sm="4" md="4" lg="4" class="my-10" align-self="center">
          <div class="text-h2 text-black font-weight-bold">
            Find all your favorite pokemon
          </div>
          <div class="mt-12 text-h5 text-black">
            You can know the type of Pokemon, its strengths disadvantages and
            abilities
          </div>
          <v-btn class="mt-4 cursor-pointer" to="/pokedex" color="success"
            >See Pokemons</v-btn
          >
        </v-col>

        <v-col cols="8" class="d-none d-sm-flex">
          <img
            class="w-100"
            src="/src/assets/banner.png"
            alt="banner pikachu"
          />
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<style scoped>
.custom-font-size {
  font-size: 42px;
}
</style>
