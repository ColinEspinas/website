<script setup lang="ts">

</script>

<template>
  <AppBentoCardBase class="aspect-square row-span-2 col-span-1 p-4 group overflow-hidden flex flex-col justify-between">
    <header>
      <h3 class="text-lg font-bold">
        Education
      </h3>
      <h4 class="text-sm">
        Where I have studied.
      </h4>
    </header>
    <UiGlobe class="h-full w-full absolute -bottom-3/12 left-6/12 -translate-x-6/12" />
    <footer class="w-full rounded-b-xl z-10">
      <div class="flex gap-2">
        <UiButton
          variant="secondary"
          shape="rounded"
          before-icon="ph:arrow-left"
        />
        <UiButton
          variant="secondary"
          shape="rounded"
          before-icon="ph:arrow-right"
        />
      </div>
    </footer>
  </AppBentoCardBase>
</template>
