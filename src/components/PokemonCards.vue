<script setup>
const pokemon = defineProps(["name", "imageUrl"]);
</script>

<template>
  <v-card class="cardPokemonList mx-auto col-4" max-width="400" width="380px">
    <v-container>
      <v-card class="cardPokemonList">
        <div class="d-flex flex-no-wrap justify-space-between">
          <div>
            <v-card-title class="text-h5">{{ pokemon?.name }}</v-card-title>
            <v-card-subtitle>Pokemon</v-card-subtitle>
          </div>

          <v-img
            height="220px"
            aspect-ratio="16/9"
            cover
            :src="pokemon?.imageUrl"
          />
        </div>
      </v-card>
    </v-container>
  </v-card>
</template>

<style scoped>
.cardPokemonList {
  background: rgb(245, 219, 19);
  background: linear-gradient(
    90deg,
    rgba(245, 219, 19, 1) 0%,
    rgba(245, 219, 19, 1) 50%,
    rgba(250, 255, 189, 1) 100%
  );
  cursor: pointer;
}
.cardPokemonList:hover {
  background: rgb(250, 235, 89);
  background: linear-gradient(
    90deg,
    rgba(250, 235, 89, 1) 0%,
    rgba(250, 235, 89, 1) 50%,
    rgba(250, 255, 189, 1) 100%
  );
}
</style>
