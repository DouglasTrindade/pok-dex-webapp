<script setup>
const pokemon = defineProps(["name", "imageUrl"]);
</script>

<template>
  <v-card class="cardPokemonList mx-auto col-4" max-width="400">
    <v-container>
      <v-card class="cardPokemonList">
        <div class="d-flex flex-no-wrap justify-space-between">
          <div>
            <v-card-title class="text-h5">{{ pokemon.name }}</v-card-title>
            <v-card-subtitle>Ellie Goulding</v-card-subtitle>
          </div>

          <v-avatar class="w-50" rounded="0" size="150">
            <v-img class="w-100" :src="pokemon.imageUrl" cover />
          </v-avatar>
        </div>
      </v-card>
    </v-container>
  </v-card>
</template>

<style scoped>
.cardPokemonList {
  background: rgb(73, 78, 19);
  background: linear-gradient(
    90deg,
    rgba(73, 78, 19, 0.9948354341736695) 36%,
    rgba(245, 239, 20, 1) 73%,
    rgba(241, 255, 0, 1) 100%
  );
  cursor: pointer;
}
.cardPokemonList:hover {
  background: rgb(40, 43, 3);
  background: linear-gradient(
    90deg,
    rgba(40, 43, 3, 0.9948354341736695) 48%,
    rgba(245, 239, 20, 1) 94%,
    rgba(241, 255, 0, 1) 100%
  );
}
</style>
