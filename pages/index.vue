<script setup lang="ts">
const { t } = useI18n()

useSeoMeta({
  title: 'test',
})

useHead({
  link: [
    { rel: 'icon', href: '/favicon.ico', sizes: '32x32' },
    { rel: 'apple-touch-icon', sizes: '180x180', href: '/apple-touch-icon.png' },
    { rel: 'icon', type: 'image/png', sizes: '32x32', href: '/favicon-32x32.png' },
    { rel: 'icon', type: 'image/png', sizes: '16x16', href: '/favicon-16x16.png' },
  ],
})
</script>

<template>
  <div class="flex justify-center w-full">
    <div class="flex flex-col gap-6 w-full items-center max-w-[600px] py-10 px-5 relative">
      <OrganismsNavigation />
      <h1 class="text-3xl" v-html="$t('home.headline')" />
    </div>
  </div>
</template>
