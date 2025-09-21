<script lang="ts" setup>
import type { COBEOptions } from 'cobe'
import createGlobe from 'cobe'
import { onBeforeUnmount, onMounted, ref } from 'vue'

const props = defineProps<{
  targetLocation: { lat: number, long: number }
  markerLocations: { lat: number, long: number }[]
}>()

const config: COBEOptions = {
  width: 2000,
  height: 2000,
  onRender: () => {},
  devicePixelRatio: 2,
  phi: locationToAngles(props.targetLocation.lat, props.targetLocation.long)[0],
  theta: locationToAngles(props.targetLocation.lat, props.targetLocation.long)[1],
  dark: 0,
  diffuse: 2,
  mapSamples: 12000,
  mapBrightness: 1.2,
  mapBaseBrightness: 0,
  baseColor: [1, 1, 1],
  markerColor: [87 / 255, 74 / 255, 226 / 255],
  glowColor: [1, 1, 1],
  scale: 1.5,
  offset: [150, 80],
  markers: props.markerLocations?.map(location => ({
    location: [location.lat, location.long],
    size: 0.07,
  })),
}

const globeCanvasRef = ref<HTMLCanvasElement>()
const width = ref(0)
const currentPhi = ref(0)
const currentTheta = ref(0)

let globe: ReturnType<typeof createGlobe> | null = null

function locationToAngles(lat: number, long: number) {
  return [Math.PI - ((long * Math.PI) / 180 - Math.PI / 2), (lat * Math.PI) / 180]
}

function onRender(state: Record<string, unknown>) {
  const doublePi = Math.PI * 2
  state.phi = currentPhi.value
  state.theta = currentTheta.value
  const [focusPhi, focusTheta] = locationToAngles(
    props.targetLocation.lat,
    props.targetLocation.long,
  )
  const distPositive = (focusPhi - currentPhi.value + doublePi) % doublePi
  const distNegative = (currentPhi.value - focusPhi + doublePi) % doublePi
  // Control the speed
  if (distPositive < distNegative) {
    currentPhi.value += distPositive * 0.08
  }
  else {
    currentPhi.value -= distNegative * 0.08
  }
  currentTheta.value = currentTheta.value * 0.92 + focusTheta * 0.08
  state.width = width.value * 2
  state.height = width.value * 2
}

function onResize() {
  if (globeCanvasRef.value) {
    width.value = globeCanvasRef.value.offsetWidth
  }
}

function createGlobeOnMounted() {
  globe = createGlobe(globeCanvasRef.value!, {
    ...config,
    width: width.value * 2,
    height: width.value * 2,
    onRender,
  })
}

onMounted(() => {
  window.addEventListener('resize', onResize)
  onResize()
  createGlobeOnMounted()

  setTimeout(() => (globeCanvasRef.value!.style.opacity = '1'))
})

onBeforeUnmount(() => {
  globe?.destroy()
  window.removeEventListener('resize', onResize)
})
</script>

<template>
  <div>
    <canvas
      ref="globeCanvasRef"
      class="size-full opacity-0 transition-opacity duration-1000 ease-in-out [contain:layout_paint_size]"
    />
  </div>
</template>
