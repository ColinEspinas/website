<script setup lang="ts">
const locations = [
  {
    country: 'France',
    city: 'Puy en Velay',
    degree: 'University Diploma in Computer Graphics',
    year: '2017 - 2020',
    lat: 45.0399745,
    long: 3.8786405,
  },
  {
    country: 'Canada',
    city: 'Matane',
    degree: 'Diploma of College Studies in Computer Science',
    year: '2020',
    lat: 48.7962387,
    long: -67.5651266,
  },
  {
    country: 'France',
    city: 'La Rochelle',
    degree: 'Professional Bachelor\'s Degree in Full-Stack Application Development',
    year: '2020 - 2021',
    lat: 46.1476498,
    long: -1.1575164,
  },
  {
    country: 'France',
    city: 'Paris',
    degree: 'Master\'s Degree in Web and Mobile Engineering',
    year: '2021 - 2023',
    lat: 48.8935752,
    long: 2.2243825,
  },
]

const currentLocationIndex = ref(0)

function getNextLocationIndex() {
  currentLocationIndex.value = (currentLocationIndex.value + 1) % locations.length
}

function getPreviousLocationIndex() {
  currentLocationIndex.value = (currentLocationIndex.value - 1 + locations.length) % locations.length
}

const currentLocation = computed(() => locations[currentLocationIndex.value])
</script>

<template>
  <AppBentoCardBase class="aspect-square row-span-2 col-span-1 p-4 group overflow-hidden flex flex-col justify-between">
    <div class="absolute inset-0 h-1/2 w-full bg-gradient-to-b from-base-100 to-transparent from-50% to-100% rounded-t-xl z-1" />
    <header class="z-2">
      <h3 class="text-lg font-bold mb-2">
        Educational Journey
      </h3>
      <div class="w-fit mb-2 flex flex-col gap-1 text-sm rounded-xl">
        <span class="font-semibold text-base-content-200 text-xs">{{ currentLocation.country }} - {{ currentLocation.city }}</span>
        <span class="font-bold">{{ currentLocation.degree }}</span>
      </div>
    </header>
    <UiGlobe
      class="h-full w-full absolute z-0 top-0 left-6/12 -translate-x-6/12"
      :target-location="locations[currentLocationIndex]"
      :marker-locations="locations"
    />
    <div class="z-10 flex flex-col gap-2">
      <span class="font-semibold text-xs text-base-content-200 bg-base-100 border-1 border-base-content-100/20 w-fit py-1 px-2 rounded-full">{{ currentLocation.year }}</span>
      <footer class="w-full flex rounded-b-xl justify-between">
        <div class="flex gap-2">
          <UiButton
            variant="secondary"
            shape="rounded"
            before-icon="ph:arrow-left"
            aria-label="Go to previous location"
            :disabled="currentLocationIndex === 0"
            @click="getPreviousLocationIndex"
          />
          <UiButton
            variant="secondary"
            shape="rounded"
            before-icon="ph:arrow-right"
            aria-label="Go to next location"
            :disabled="currentLocationIndex === locations.length - 1"
            @click="getNextLocationIndex"
          />
        </div>
        <div class="flex gap-2">
          <UiButton
            variant="secondary"
            shape="rounded"
            before-icon="ph:eye"
            text="See more"
            to="/"
          />
        </div>
      </footer>
    </div>
  </AppBentoCardBase>
</template>
