<script setup lang="ts">
import { UseImage } from '@vueuse/components'
</script>

<template>
  <AppBentoCardBase class="row-span-2 col-span-1 !p-0 group aspect-square">
    <UseImage
      src="images/me.jpg"
      alt="Photo de moi"
      class="rounded-xl w-full h-full aspect-square object-cover select-none bg-base-200"
    >
      <template #loading>
        <div class="rounded-xl w-full h-auto aspect-square object-cover select-none bg-base-300 animate-pulse" />
      </template>
    </UseImage>
    <UseImage
      src="svg/me.svg"
      alt="Me arrow"
      class="absolute -bottom-6 left-9/12"
    />
  </AppBentoCardBase>
</template>
