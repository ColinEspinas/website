<script setup lang="ts">
// maybe add "ring-0 ring-base-content-100/10 hover:ring-3 transition-all" to classes ?
</script>

<template>
  <article
    class="relative flex flex-col rounded-xl bg-base-100 border-1 border-base-content-100/20 p-2 animate-fade-in"
  >
    <slot />
  </article>
</template>
