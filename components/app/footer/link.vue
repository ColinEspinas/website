<script setup lang="ts">
withDefaults(defineProps<{
  to: string
  external?: boolean
  target?: '_blank' | '_self'
  text: string
}>(), {
  external: false,
  target: '_self',
})
</script>

<template>
  <NuxtLink
    :to
    :target
    :external
    class="font-bold text-base-content-200 hover:text-base-content-100 transition-colors"
  >
    {{ text }}
  </NuxtLink>
</template>
