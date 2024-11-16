<template>
  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<style>
#app {
  font-family: "Arial", sans-serif;
  color: var(--var-soft-gray);
  line-height: 1.6;
  text-align: center;
  margin: 0;
  padding: 0;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background-color: #f9f9f9;
}
</style>
