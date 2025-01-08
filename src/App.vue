<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
        <nav>
        <RouterLink to="/">Startsida</RouterLink>
        <RouterLink to="/data">Data</RouterLink>
        <RouterLink to="/about">Om Vue.js</RouterLink>
      </nav>
  <RouterView />
</template>

<style scoped>
</style>
