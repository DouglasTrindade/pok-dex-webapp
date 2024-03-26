<script setup>
const icons = ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"];
</script>

<template>
  <v-footer class="d-flex flex-column" style="background-color: #000000">
    <div class="d-flex align-center justify-content-center px-4">
      <v-btn
        v-for="icon in icons"
        :key="icon"
        :icon="icon"
        class="mx-4"
        size="small"
        variant="plain"
      ></v-btn>
    </div>

    <div class="px-4 py-2 bg-black text-center w-100 mt-auto">
      {{ new Date().getFullYear() }} — <strong>Douglas Trindade</strong>
    </div>
  </v-footer>
</template>

<style scoped></style>
