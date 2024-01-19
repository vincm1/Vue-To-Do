<script setup>
import { RouterLink, RouterView } from 'vue-router';
import HomeView from './views/HomeView.vue';
</script>

<template>
  <HomeView />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #555;
}

body {
  background: #f2f2f2;
}

</style>
