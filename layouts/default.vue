<script setup lang="ts">
const localeHead = useLocaleHead()
useHead({
  htmlAttrs: {
    lang: localeHead.value.htmlAttrs.lang,
  },
})
</script>

<template>
  <div>
    <AppNavigation />
    <div class="flex flex-col max-w-[500px] md:max-w-[640px] mx-auto px-10 md:px-0">
      <div
        class="absolute inset-0 h-full w-full -z-50 bg-transparent mask-radial-at-top mask-radial-[50%_50%] mask-radial-from-10% bg-[linear-gradient(to_right,var(--color-base-200)_1px,transparent_1px),linear-gradient(to_bottom,var(--color-base-200)_1px,transparent_1px)] bg-[size:24px_24px]"
      />
      <main>
        <slot />
      </main>
    </div>
    <AppFooter />
  </div>
</template>
