<template>
  <NuxtPage />

  <AuthOverlay v-if="$generalStore.isLoginOpen"></AuthOverlay>
</template>

<script setup>
const { $generalStore } = useNuxtApp()
</script>
