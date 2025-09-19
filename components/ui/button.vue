<script setup lang="ts">
import { useMouseInElement } from '@vueuse/core'

withDefaults(defineProps<{
  text?: string
  afterIcon?: string
  beforeIcon?: string
  type?: 'button' | 'submit' | 'reset'
  disabled?: boolean
  variant?: 'primary' | 'secondary' | 'accent' | 'glass'
  align?: 'left' | 'center' | 'right'
  shape?: 'rounded' | 'default'
  to?: string
  target?: '_blank' | '_self'
  external?: boolean
}>(), {
  type: 'button',
  disabled: false,
  variant: 'primary',
  align: 'left',
  shape: 'default',
  external: false,
})

const emits = defineEmits<{
  click: []
}>()

const variantClasses = {
  primary: 'bg-base-content-100 text-base-100 ring-0 border-1 border-transparent ring-base-content-100/20 hover:ring-3 transition-all',
  secondary: 'bg-base-100/60 text-base-content-100  border-1 border-base-content-100/20 ring-0 ring-base-content-100/10 hover:ring-3 transition-all',
  accent: 'bg-accent text-accent-content ring-0 ring-accent/25 hover:ring-3 border-1 border-accent transition-all bg-radial-(--gradient-position) from-base-100/20 to-transparent to-50%',
  glass: 'bg-base-100/40 backdrop-blur-md shadow-md text-base-content-100 border-1 border-base-content-100/5 ring-0 ring-base-content-100/10 hover:ring-3 transition-all bg-radial-(--gradient-position) from-base-100/20 to-transparent to-50%',
}

const alignClasses = {
  left: 'justify-start',
  center: 'justify-center',
  right: 'justify-end',
}

const shapeClasses = {
  rounded: 'rounded-full',
  default: 'rounded-lg',
}

const buttonRef = useTemplateRef<HTMLDivElement>('button')
const { elementX, elementY, elementHeight, elementWidth } = useMouseInElement(buttonRef)

const gradientPosition = computed(() => {
  // If mouse is not near the edges, don't show the gradient
  const padding = 100
  if (elementX.value > -padding && elementX.value < elementWidth.value + padding
    && elementY.value > -padding && elementY.value < elementHeight.value + padding) {
    return `circle at ${elementX.value}px ${elementY.value}px`
  }
  return ''
})
</script>

<template>
  <NuxtLink
    v-if="to"
    ref="button"
    :to="to"
    class="py-2 px-3 flex gap-2 items-center outline-none font-medium active:scale-95 cursor-pointer"
    :class="[variantClasses[variant], alignClasses[align], shapeClasses[shape]]"
    :style="{ '--gradient-position': gradientPosition }"
    :target="target"
    :external
  >
    <Icon v-if="beforeIcon" class="my-1" :size="18" :name="beforeIcon" />
    <span v-if="text">{{ text }}</span>
    <Icon v-if="afterIcon" class="my-1" :size="18" :name="afterIcon" />
  </NuxtLink>
  <button
    v-else
    ref="button"
    class="py-2 px-3 flex gap-2 items-center outline-none font-medium active:scale-95 cursor-pointer"
    :style="{ '--gradient-position': gradientPosition }"
    :disabled="disabled"
    :class="[variantClasses[variant], alignClasses[align], shapeClasses[shape]]"
    :type="type"
    @click="emits('click')"
  >
    <Icon v-if="beforeIcon" class="my-1" :size="18" :name="beforeIcon" />
    <span v-if="text">{{ text }}</span>
    <Icon v-if="afterIcon" class="my-1" :size="18" :name="afterIcon" />
  </button>
</template>
