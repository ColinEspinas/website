<script lang="ts" setup>
import type { COBEOptions } from 'cobe'
import createGlobe from 'cobe'
import { onBeforeUnmount, onMounted, ref } from 'vue'

interface GlobeProps {
  config?: Partial<COBEOptions>
  mass?: number
  tension?: number
  friction?: number
  precision?: number
}

const props = withDefaults(defineProps<GlobeProps>(), {
  mass: 1,
  tension: 280,
  friction: 100,
  precision: 0.001,
})

const DEFAULT_CONFIG: COBEOptions = {
  width: 800,
  height: 800,
  onRender: () => {},
  devicePixelRatio: 2,
  phi: 5.2,
  theta: 0.1,
  dark: 0,
  diffuse: 0.4,
  mapSamples: 42000,
  mapBrightness: 1.2,
  baseColor: [1, 1, 1],
  markerColor: [251 / 255, 100 / 255, 21 / 255],
  glowColor: [1.2, 1.2, 1.2],
  scale: 2,
  offset: [0, 200],
  markers: [
    { location: [48.8935752, 2.2243825], size: 0.08 },
    { location: [48.7962387, -67.5651266], size: 0.08 },
    { location: [46.1476498, -1.1575164], size: 0.08 },
    { location: [45.0399745, 3.8786405], size: 0.08 },
  ],
}

const globeCanvasRef = ref<HTMLCanvasElement>()
const width = ref(0)

let globe: ReturnType<typeof createGlobe> | null = null

function onRender(state: Record<string, unknown>) {
  state.width = width.value * 2
  state.height = width.value * 2
}

function onResize() {
  if (globeCanvasRef.value) {
    width.value = globeCanvasRef.value.offsetWidth
  }
}

function createGlobeOnMounted() {
  const config = { ...DEFAULT_CONFIG, ...props.config }

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
