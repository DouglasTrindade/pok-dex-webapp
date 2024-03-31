<script setup>
import SvgIcon from "@jamescoyle/vue-icon";
import { mdiWindowClose } from "@mdi/js";
import PokemonCards from "../components/PokemonCards.vue";
import NavBar from "@/components/NavBar.vue";
import { onMounted, ref, computed } from "vue";

const imageUrl = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
);
const pokemonList = ref([]);
const searchPokemonField = ref("");
const isDialogOpen = ref(false);
const selectedPokemon = ref(null);
const path = mdiWindowClose;

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then((res) => res.json())
    .then((data) => {
      pokemonList.value = data.results;
    });
});

const pokemonsFiltered = computed(() => {
  if (!pokemonList.value) return [];

  return pokemonList.value.filter((pokemon) =>
    pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
  );
});

const openModal = async (pokemon) => {
  try {
    const res = await fetch(pokemon.url);
    const data = await res.json();

    selectedPokemon.value = {
      name: data.name,
      imageUrl: imageUrl.value + data.id + pokemon.url.split("/")[7] + ".svg",
      abilities: data.abilities.map((ability) => ability.ability.name),
      hp: data.stats.find((stat) => stat.stat.name === "hp").base_stat,
      experience: data.base_experience,
      attack: data.stats.find((stat) => stat.stat.name === "attack").base_stat,
      defense: data.stats.find((stat) => stat.stat.name === "defense")
        .base_stat,
      specialAttack: data.stats.find(
        (stat) => stat.stat.name === "special-attack"
      )?.base_stat,
      specialDefense: data.stats.find(
        (stat) => stat.stat.name === "special-defense"
      )?.base_stat,
    };

    isDialogOpen.value = true;
  } catch (error) {
    console.error("Erro ao carregar detalhes do Pokémon:", error);
  }
};

const closeModal = () => {
  isDialogOpen.value = false;
};
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
      <v-row justify="center">
        <v-col cols="10">
          <v-text-field
            v-model="searchPokemonField"
            label="Search for a pokemon"
            color="black"
            class="text-black"
          />
        </v-col>
      </v-row>
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          v-for="pokemon in pokemonsFiltered"
          :key="pokemon.name"
        >
          <PokemonCards
            @click="openModal(pokemon)"
            :name="pokemon.name"
            :imageUrl="imageUrl + pokemon.url.split('/').slice(-2)[0] + '.svg'"
          />
        </v-col>
      </v-row>
    </v-container>

    <v-dialog max-width="800px" v-model="isDialogOpen">
      <v-card class="overflow-hidden" rounded="lg">
        <div class="d-flex justify-end">
          <svg-icon
            class="cursor-pointer mx-3 my-3"
            @click="closeModal"
            type="mdi"
            :path="path"
          />
        </div>
        <v-card-text>
          <div v-if="selectedPokemon">
            <v-row>
              <v-col>
                <img
                  :src="selectedPokemon.imageUrl"
                  alt="pokemon"
                  width="300px"
                  height="300px"
                />
              </v-col>
              <v-col>
                <div class="text-h3 font-weight-medium text-capitalize">
                  {{ selectedPokemon.name }}
                </div>
                <v-card class="mt-6 w-75 py-2 px-8" color="#FFFFFF">
                  <div class="font-weight-medium text-h6">Abilities</div>
                  <div class="text-capitalize">
                    {{ selectedPokemon.abilities.join(" - ") }}
                  </div></v-card
                >

                <v-card class="mt-6 py-2 px-8" color="#FFFFFF">
                  <v-row>
                    <v-col cols="6">
                      <div class="font-weight-medium text-h6">
                        Health Points
                      </div>
                      <div class="text-capitalize">
                        {{ selectedPokemon.hp - 1 + "00000" }}
                      </div>
                      <img src="/green-line.png" alt="" />
                    </v-col>
                    <v-col cols="6">
                      <div class="font-weight-medium text-h6">Experience</div>
                      <div class="text-capitalize">
                        {{ selectedPokemon.experience - 1 + "00000" }}
                      </div>
                      <img src="/yellow-line.png" alt="" />
                    </v-col>
                  </v-row>
                </v-card>
                <div class="d-flex ga-4">
                  <v-card
                    class="mt-6 py-4 text-center"
                    color="#FFFFFF"
                    style="width: 95px"
                  >
                    <v-chip color="primary" variant="outlined">
                      <div class="text-h6">
                        {{ selectedPokemon.attack }}
                      </div>
                    </v-chip>
                    <div class="text-caption mt-2 font-weight-medium">
                      Attack
                    </div>
                  </v-card>
                  <v-card
                    class="mt-6 py-4 text-center"
                    color="#FFFFFF"
                    style="width: 95px"
                  >
                    <v-chip color="primary" variant="outlined">
                      <div class="text-h6">
                        {{ selectedPokemon.defense }}
                      </div>
                    </v-chip>
                    <div class="text-caption mt-2 font-weight-medium">
                      Defense
                    </div>
                  </v-card>
                  <v-card
                    class="mt-6 py-4 text-center"
                    color="#FFFFFF"
                    style="width: 95px"
                  >
                    <v-chip color="primary" variant="outlined">
                      <div class="text-h6">
                        {{ selectedPokemon.specialAttack }}
                      </div>
                    </v-chip>
                    <div class="text-caption mt-2 font-weight-medium">
                      Sp Attack
                    </div>
                  </v-card>
                  <v-card
                    class="mt-6 py-4 text-center"
                    color="#FFFFFF"
                    style="width: 95px"
                  >
                    <v-chip color="primary" variant="outlined">
                      <div class="text-h6">
                        {{ selectedPokemon.specialDefense }}
                      </div>
                    </v-chip>
                    <div class="text-caption mt-2 font-weight-medium">
                      Sp Defense
                    </div>
                  </v-card>
                </div>
              </v-col>
            </v-row>
          </div>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-main>
</template>

<style></style>
