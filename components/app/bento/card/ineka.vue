<script lang="ts" setup>

</script>

<template>
  <AppBentoCardBase class="row-span-1 col-span-1 p-4 group overflow-hidden flex flex-col justify-between gap-4">
    <header>
      <h3 class="text-lg font-bold">
        Ineka
      </h3>
      <h4 class="text-sm">
        A modular Typescript game engine.
      </h4>
    </header>
    <footer class="w-full rounded-b-xl">
      <div class="flex gap-2">
        <UiButton
          variant="secondary"
          shape="rounded"
          before-icon="ph:play"
          to="https://bibliopus.app"
          target="_blank"
          external
        />
        <UiButton
          variant="secondary"
          shape="rounded"
          before-icon="ph:code"
        />
      </div>
    </footer>
  </AppBentoCardBase>
</template>
