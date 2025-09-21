<script setup lang="ts">
import { useMouseInElement } from '@vueuse/core'

const navRef = useTemplateRef<HTMLDivElement>('nav')
const { elementX, elementY, elementHeight, elementWidth } = useMouseInElement(navRef)

const gradientPosition = computed(() => {
  // If mouse is not near the edges, don't show the gradient
  const padding = 100
  if (elementX.value > -padding && elementX.value < elementWidth.value + padding
    && elementY.value > -padding && elementY.value < elementHeight.value + padding) {
    return `circle at ${elementX.value}px ${elementY.value}px`
  }
  return ''
})
</script>

<template>
  <nav class="fixed bottom-0 left-0 w-full flex justify-end z-50">
    <div class="absolute -bottom-5 left-0 w-full h-40">
      <div class="absolute inset-0 backdrop-blur-[0.1875px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent,black_12.5%,black_25%,transparent_37.5%)]" />
      <div class="absolute inset-0 backdrop-blur-[0.375px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_12.5%,black_25%,black_37.5%,transparent_50%)]" />
      <div class="absolute inset-0 backdrop-blur-[0.75px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_25%,black_37.5%,black_50%,transparent_62.5%)]" />
      <div class="absolute inset-0 backdrop-blur-[1.5px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_37.5%,black_50%,black_62.5%,transparent_75%)]" />
      <div class="absolute inset-0 backdrop-blur-[3px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_50%,black_62.5%,black_75%,transparent_87.5%)]" />
      <div class="absolute inset-0 backdrop-blur-[6px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_62.5%,black_75%,black_87.5%,transparent_100%)]" />
      <div class="absolute inset-0 backdrop-blur-[12px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_75%,black_87.5%,black_100%,transparent_100%)]" />
      <div class="absolute inset-0 backdrop-blur-[24px] h-full w-full bg-transparent mask-[linear-gradient(to_bottom,transparent_87.5%,black_100%,black_100%,transparent_100%)]" />
    </div>
    <ul
      ref="nav"
      class="flex gap-2 mx-auto z-50 bg-base-300/40 backdrop-blur-xl p-2 rounded-full border-1 border-base-content-200/5 mb-6 shadow-2xl bg-radial-(--gradient-position) from-base-100/20 to-transparent to-50%"
      :style="{ '--gradient-position': gradientPosition }"
    >
      <li>
        <UiButton
          variant="ghost"
          size="lg"
          shape="rounded"
          before-icon="ph:house-duotone"
          to="/"
          class="text-base font-medium hover:underline"
        />
      </li>
      <li>
        <UiButton
          variant="ghost"
          shape="rounded"
          size="lg"
          before-icon="ph:hand-waving-duotone"
          to="/about"
          class="text-base font-medium hover:underline"
        />
      </li>
      <li>
        <UiButton
          variant="ghost"
          shape="rounded"
          size="lg"
          before-icon="ph:mailbox-duotone"
          to="/contact"
          class="text-base font-medium hover:underline"
        />
      </li>
      <li>
        <UiButton
          variant="ghost"
          shape="rounded"
          size="lg"
          before-icon="ph:moon-duotone"
          class="text-base font-medium hover:underline"
        />
      </li>
    </ul>
  </nav>
</template>
