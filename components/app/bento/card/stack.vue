<script setup lang="ts">
const icons = [
  'simple-icons:nuxt',
  'simple-icons:vuedotjs',
  'simple-icons:typescript',
  'simple-icons:javascript',
  'simple-icons:tailwindcss',
  'simple-icons:css3',
  'simple-icons:html5',
  'simple-icons:graphql',
  'simple-icons:prisma',
  'simple-icons:postgresql',
  'simple-icons:docker',
  'simple-icons:git',
]

const logoWidth = 32
const gap = 24
</script>

<template>
  <AppBentoCardBase class="row-span-1 col-span-1 p-4 group overflow-hidden">
    <header class="mb-2">
      <h3 class="text-lg font-bold">
        Tech I have worked with
      </h3>
    </header>
    <div class="h-full w-full mx-auto overflow-hidden relative select-none touch-none mask-radial-at-center mask-radial-[50%_150%] mask-radial-from-50% mask-radial-from-black mask-radial-to-transparent">
      <div
        class="h-full flex animate-infinite-slider w-[calc(var(--slide-width)*var(--logo-set-count)*var(--slide-count))] group-hover:[animation-play-state:paused]"
        :style="{
          '--slide-width': `${logoWidth + gap}px`,
          '--slide-count': icons.length,
          '--logo-set-count': 2,
          '--logo-width': `${logoWidth}px`,
        }"
      >
        <div
          v-for="(icon, index) in [...icons, ...icons]"
          :key="index"
          class="flex items-center justify-center w-[var(--slide-width)] hover:scale-110 transition-transform duration-300"
          :class="index % 2 === 0 ? 'hover:rotate-6' : 'hover:-rotate-6'"
        >
          <div class="flex bg-base-200 rounded-lg p-2">
            <Icon
              :name="icon"
              :size="logoWidth"
              class="text-base-content-100"
            />
          </div>
        </div>
      </div>
    </div>
  </AppBentoCardBase>
</template>
