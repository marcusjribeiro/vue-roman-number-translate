<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import "./index.css";
</script>

<template>
  <header>
    <div class="wrapper">
      <h1 class="text-2xl font-bold text-emerald-400">
        Roman numbers to integers
      </h1>

      <nav class="w-full text-base text-left mt-8 align-middle mb-12">
        <RouterLink class="pr-4 font-medium hover:text-emerald-400" to="/"
          >Roman to Integer</RouterLink
        >
        <RouterLink
          class="hover:text-emerald-400 font-medium px-4 border-l border-l-gray-600"
          to="/inverse"
          >Integer to Roman</RouterLink
        >
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  max-height: 100vh;
}
</style>
