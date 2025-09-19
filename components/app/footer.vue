<script setup lang="ts">
const { y } = useWindowScroll({ behavior: 'smooth' })
</script>

<template>
  <footer class="relative mt-30">
    <div class="absolute -z-50 bottom-full left-0 w-full h-[240px] border-b border-base-200 mask-radial-at-bottom mask-radial-[50%_50%] mask-radial-from-10% bg-[linear-gradient(to_right,var(--color-base-200)_1px,transparent_1px),linear-gradient(to_bottom,var(--color-base-200)_1px,transparent_1px)] bg-[size:24px_24px]" />
    <div class="flex flex-col max-w-[600px] mx-auto px-10 py-10">
      <nav class="flex justify-between">
        <div class="flex gap-10 font-bold text-base-content-200">
          <div class="flex flex-col gap-2">
            <NuxtLink to="/" class="">
              Home
            </NuxtLink>
            <NuxtLink to="/" class="">
              About
            </NuxtLink>
            <NuxtLink to="/" class="">
              Work
            </NuxtLink>
            <NuxtLink to="/" class="">
              Contact
            </NuxtLink>
          </div>
          <div class="flex flex-col gap-2">
            <NuxtLink to="/" class="">
              Home
            </NuxtLink>
            <NuxtLink to="/" class="">
              About
            </NuxtLink>
            <NuxtLink to="/" class="">
              Work
            </NuxtLink>
            <NuxtLink to="/" class="">
              Contact
            </NuxtLink>
          </div>
        </div>
        <div class="flex flex-col">
          <UiButton
            variant="secondary"
            before-icon="ph:arrow-up"
            text="Go back up"
            @click="y = 0"
          />
        </div>
      </nav>
      <p class="text-sm text-base-content-200 font-semibold mt-10">
        © 2024 Colin Espinas. All rights reserved.
      </p>
    </div>
  </footer>
</template>
