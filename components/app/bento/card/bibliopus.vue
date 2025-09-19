<script setup lang="ts">
const covers = [
  'https://covers.openlibrary.org/b/isbn/1794329897-L.jpg',
  'https://covers.openlibrary.org/b/isbn/9782330155582-L.jpg',
  'https://covers.openlibrary.org/b/isbn/9782266239288-L.jpg',
]
</script>

<template>
  <AppBentoCardBase class="aspect-square row-span-2 col-span-1 p-4 group overflow-hidden">
    <header>
      <h3 class="text-lg font-bold">
        Bibliopus
      </h3>
      <h4 class="text-sm">
        Keep track of your reading.
      </h4>
    </header>
    <div>
      <UiBookCollection
        :id="75"
        :covers="covers"
        class="absolute bottom-0 left-0 z-0"
      />
    </div>
    <footer class="absolute z-10 bottom-0 left-0 p-4 bg-gradient-to-t from-base-content-100/50 to-base-content-100/0 to-100% w-full rounded-b-xl">
      <div class="flex gap-2">
        <UiButton
          variant="glass"
          shape="rounded"
          before-icon="ph:arrow-square-out"
          to="https://bibliopus.app"
          target="_blank"
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
