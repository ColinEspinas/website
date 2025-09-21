<script setup lang="ts">
const covers = [
  {
    src: 'https://covers.openlibrary.org/b/isbn/1794329897-L.jpg',
    url: 'https://shelf.bibliopus.app/editions/1794329897',
  },
  {
    src: 'https://covers.openlibrary.org/b/isbn/9782330155582-L.jpg',
    url: 'https://shelf.bibliopus.app/editions/9782330155582',
  },
  {
    src: 'https://covers.openlibrary.org/b/isbn/9782266239288-L.jpg',
    url: 'https://shelf.bibliopus.app/editions/9782266239288',
  },
]
</script>

<template>
  <AppBentoCardBase class="aspect-square row-span-2 col-span-1 p-4 group overflow-hidden">
    <header class="z-1">
      <h3 class="text-lg font-bold">
        Bibliopus
      </h3>
      <h4 class="text-sm">
        Keep track of your reading.
      </h4>
    </header>
    <UiBookCollection
      :id="75"
      :covers="covers"
      class="absolute bottom-0 left-0 z-0"
    />
    <footer class="absolute z-3 bottom-0 left-0 p-4 bg-gradient-to-t from-base-content-100/50 to-base-content-100/0 to-100% w-full rounded-b-xl">
      <div class="flex gap-2">
        <UiButton
          variant="glass"
          shape="rounded"
          before-icon="ph:arrow-square-out"
          to="https://bibliopus.app"
          target="_blank"
          text="Visit"
          external
        />
        <UiButton
          variant="glass"
          shape="rounded"
          before-icon="ph:github-logo"
        />
      </div>
    </footer>
  </AppBentoCardBase>
</template>
