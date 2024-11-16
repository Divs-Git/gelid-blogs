<template>
  <h2 class="title">{{ blog.title }}</h2>
  <p class="desc">{{ blog.body }}</p>
</template>

<script setup>
defineProps(["blog"]);
</script>

<style scoped>
.title {
  color: var(--var-dark-green);
}
</style>
