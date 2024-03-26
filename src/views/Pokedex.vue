<script setup>
import PokemonCards from "../components/PokemonCards.vue";
import NavBar from "@/components/NavBar.vue";
import { onMounted, reactive, ref } from "vue";

const imageUrl = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
);
const pokemonList = reactive(ref());

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then((res) => res.json())
    .then((res) => (pokemonList.value = res.results));
});
console.log(pokemonList);
</script>

<template>
  <v-main>
    <NavBar />

    <div
      class="d-flex justify-center align-center font-weight-medium text-h4 text-black"
    >
      151 Pokemons for you to choose your favorite
    </div>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
          v-for="pokemon in pokemonList"
          :key="pokemon.name"
        >
          <PokemonCards
            :name="pokemon.name"
            :imageUrl="imageUrl + pokemon.url.split('/')[6] + '.svg'"
          />
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<style></style>
