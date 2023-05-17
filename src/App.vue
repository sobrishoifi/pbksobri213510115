<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div>
      <nav class="text-center pt-5">
        <RouterLink class="p-2.5 font-medium text-sm mr-2 text-white bg-blue-600 hover:bg-blue-800 rounded-lg" to="/">Home</RouterLink>
        <RouterLink class="p-2.5 font-medium text-sm mr-2 text-white bg-blue-600 hover:bg-blue-800 rounded-lg" to="/aplikasi">AplikasiKu</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
nav a.router-link-exact-active {
  @apply bg-blue-800;
  @apply text-white;
}

nav a.router-link-exact-active:hover {
  @apply bg-blue-500;
}


</style>
