<script setup>
useHead({
    titleTemplate: (titleChunk) => {
      return titleChunk ? `${titleChunk} - Random IT Ninja` : 'Random IT Ninja'
    }
})
</script>

<template>
  <div class="h-full">
    <Navbar></Navbar>
    <NuxtPage></NuxtPage>
  </div>
</template>