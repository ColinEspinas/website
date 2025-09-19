<script setup lang="ts">
import { breakpointsTailwind } from '@vueuse/core'

const slots = useSlots()
const { width } = useWindowSize()

// Récupérer les éléments du slot par défaut
const slotElements = computed(() => {
  const defaultSlotContent = slots.default?.()
  if (!defaultSlotContent)
    return []

  return defaultSlotContent.filter(vnode => vnode.type !== Comment)
})

// Ordre dynamique selon la taille d'écran
const orderedElements = computed(() => {
  const elements = slotElements.value

  if (width.value < breakpointsTailwind.md) {
    return elements
  }
  else {
    return elements
  }
})
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 grid-flow-dense auto-rows-fr gap-6">
    <component
      :is="element"
      v-for="(element, index) in orderedElements"
      :key="index"
    />
  </div>
</template>
