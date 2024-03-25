<template>
  <div class="home-container">
    <v-container>
      <NavBar />

      <v-row>
        <v-col cols="6" class="my-10">
          <div class="text-h2 text-black font-weight-bold">
            Find all your favorite pokemon
          </div>
          <div class="mt-12 text-h5 text-black">
            You can know the type of Pokemon, its strengths disadvantages and
            abilities
          </div>
        </v-col>

        <v-col cols="6" class="w-100">
          <img src="/src/assets/banner.png" alt="banner pikachu" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { onMounted, reactive } from "vue";
import NavBar from "@/components/NavBar.vue";

export default {
  name: "Home",
  components: {
    NavBar,
  },
  setup() {
    const state = reactive({
      loading: false,
      pokemonList: [],
    });

    onMounted(() => {
      state.loading = true;
      fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
        .then((res) => res.json())
        .then((res) => {
          state.pokemonList = res.results;
          state.loading = false;
          console.log(res.results);
        })
        .catch((error) => {
          console.error("Erro ao buscar dados:", error);
          state.loading = false;
        });
    });

    return {
      ...state,
    };
  },
};
</script>

<style scoped>
.home-container {
  background-color: #f5db13;
}

.custom-font-size {
  font-size: 42px;
}
</style>
