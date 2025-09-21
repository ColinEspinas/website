<script setup lang="ts">
useHead({
  title: 'Colin Espinas',
  meta: [
    {
      name: 'description',
      content: 'A developer focused on crafting tools and experiences to make the web more open, accessible and beautiful.',
    },
  ],
})
</script>

<template>
  <div class="flex flex-col gap-28 mt-28">
    <AppHeader />
    <AppBento>
      <AppBentoCardBibliopus />
      <AppBentoCardStack />
      <AppBentoCardMe />
      <AppBentoCardEducation />
      <AppBentoCardIneka />
    </AppBento>
    <AppContact />
  </div>
</template>
