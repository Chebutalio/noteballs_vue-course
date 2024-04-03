<script setup>
import NavBar from "@/components/layouts/NavBar.vue";

</script>

<template>
  <NavBar></NavBar>

  <div class="container is-max-desktop px-2 py-4">
    <RouterView></RouterView>
  </div>
</template>

<style>
@import "bulma/css/bulma.min.css";
</style>
