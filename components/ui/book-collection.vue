<script setup lang="ts">
import { UseImage } from '@vueuse/components'

withDefaults(defineProps<{
  id: number
  covers?: { src: string, url: string, alt: string }[]
}>(), {
  covers: () => [],
})
</script>

<template>
  <div class="group block h-full w-full">
    <div
      class="absolute -bottom-4 flex justify-center items-end -space-x-10 w-full h-[calc(90%-68px)]"
    >
      <NuxtLink
        v-if="covers[0]"
        class="relative rounded h-full object-cover aspect-[180/270] -rotate-6 z-10 hover:-translate-y-2 transition-transform"
        :to="covers[0]?.url"
        external
        target="_blank"
        aria-label="View book on Bibliopus"
      >
        <UseImage
          :src="covers[0].src"
          :alt="covers[0].alt"
          class="relative rounded h-full object-cover aspect-[180/270] select-none bg-base-200 animate-fade-in"
        >
          <template #loading>
            <div
              class="relative rounded h-full w-full select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
      </NuxtLink>
      <NuxtLink
        v-if="covers[1]"
        class="relative rounded h-full bottom-2 object-cover aspect-[180/270] z-10 hover:-translate-y-2 transition-transform"
        :to="covers[1]?.url"
        external
        target="_blank"
        aria-label="View book on Bibliopus"
      >
        <UseImage
          :src="covers[1].src"
          :alt="covers[1].alt"
          class="relative rounded h-full object-cover aspect-[180/270] z-20 mb-1 select-none bg-base-200 animate-fade-in"
        >
          <template #loading>
            <div
              class="relative rounded h-full w-full select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
      </NuxtLink>
      <NuxtLink
        v-if="covers[2]"
        class="relative rounded h-full object-cover aspect-[180/270] rotate-6 z-10 hover:-translate-y-2 transition-transform"
        :to="covers[2]?.url"
        external
        target="_blank"
        aria-label="View book on Bibliopus"
      >
        <UseImage
          :src="covers[2].src"
          :alt="covers[2].alt"
          class="relative rounded h-full object-cover aspect-[180/270] z-30 select-none bg-base-200 animate-fade-in "
        >
          <template #loading>
            <div
              class="relative rounded h-full w-full select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
      </NuxtLink>
    </div>
  </div>
</template>
