<script setup lang="ts">
import { UseImage } from '@vueuse/components'

withDefaults(defineProps<{
  id: number
  covers?: string[]
}>(), {
  covers: () => [],
})
</script>

<template>
  <NuxtLink
    :to="`https://shelf.bibliopus.app/collections/${id}`"
    class="group block cursor-pointer w-full"
    external
    target="_blank"
  >
    <div class="h-[150px] w-full overflow-visible">
      <div
        class="flex justify-center px-2 items-end -space-x-10"
      >
        <UseImage
          v-if="covers[0]"
          :src="covers[0]"
          class="relative rounded h-[170px] object-cover aspect-[180/270] -rotate-6 z-10 select-none bg-base-200 animate-fade-in hover:-translate-y-2 transition-transform"
        >
          <template #loading>
            >
            <div
              class="relative rounded h-[170px] object-cover aspect-[180/270] -rotate-6 z-10 select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
        <UseImage
          v-if="covers[1]"
          :src="covers[1]"
          class="relative rounded h-[170px] object-cover aspect-[180/270] z-20 mb-1 select-none bg-base-200 animate-fade-in hover:-translate-y-2 transition-transform"
        >
          <template #loading>
            >
            <div
              class="relative rounded h-[170px] object-cover aspect-[180/270] z-20 mb-1 select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
        <UseImage
          v-if="covers[2]"
          :src="covers[2]"
          class="relative rounded h-[170px] object-cover aspect-[180/270] rotate-6 z-30 select-none bg-base-200 animate-fade-in hover:-translate-y-2 transition-transform"
        >
          <template #loading>
            >
            <div
              class="relative rounded h-[170px] object-cover aspect-[180/270] rotate-6 z-30 select-none bg-base-300 animate-pulse"
            />
          </template>
        </UseImage>
      </div>
    </div>
  </NuxtLink>
</template>
