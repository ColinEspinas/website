<script setup lang="ts">
interface Link {
  to: string
  text: string
  icon: string
  external?: boolean
}

const links: Link[] = [
  { to: '/', text: 'Home', icon: 'ph:house-bold' },
  { to: '/about', text: 'About', icon: 'ph:hand-bold' },
]
</script>

<template>
  <nav class="sticky top-0 left-0 bg-base-800 rounded-full flex w-full mt-4 border-2 border-base-100/10">
    <div class="p-2">
      <AvatarRoot class="bg-base-900 border-4 border-base-900 h-[45px] w-[45px] inline-flex select-none items-center justify-center overflow-hidden rounded-full align-middle">
        <AvatarImage
          class="h-full w-full rounded-[inherit] object-cover"
          src="/img/avatar-bust.png"
          alt="Colin Espinas Avatar"
        />
        <AvatarFallback
          class="text-grass11 leading-1 flex h-full w-full items-center justify-center bg-white text-[15px] font-medium"
          :delay-ms="600"
        >
          CE
        </AvatarFallback>
      </AvatarRoot>
    </div>
    <div class="flex justify-between items-center p-2">
      <ul class="flex items-center gap-2 h-full">
        <li v-for="(link, index) in links" :key="index" class="h-full">
          <NuxtLink
            :to="link.to"
            class="text-base-100 flex items-center gap-1 px-3 h-full rounded-full bg-base-100/10 border-2 border-base-100/10"
          >
            <Icon :name="link.icon" :size="18" />
            <span class="text-lg">{{ link.text }}</span>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>
