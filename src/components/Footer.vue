<script setup>
const icons = ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"];
</script>

<template>
  <v-footer
    class="d-flex flex-column justify-center align-center w-100"
    style="background-color: #000000"
  >
    <div class="px-4">
      <v-btn
        v-for="icon in icons"
        :key="icon"
        :icon="icon"
        class="mx-4"
        size="small"
        variant="plain"
      ></v-btn>
    </div>

    <div class="px-4 py-2 bg-black w-100 mt-auto text-center">
      {{ new Date().getFullYear() }} — <strong>Douglas Trindade</strong>
    </div>
  </v-footer>
</template>

<style scoped></style>
