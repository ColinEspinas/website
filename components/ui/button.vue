<script setup lang="ts">
import { useMouseInElement } from '@vueuse/core'

withDefaults(defineProps<{
  text?: string
  afterIcon?: string
  beforeIcon?: string
  type?: 'button' | 'submit' | 'reset'
  disabled?: boolean
  variant?: 'primary' | 'secondary' | 'accent'
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
  primary: 'bg-base-content-100 base-100 ring-0 border-1 border-transparent ring-base-content-100/20 hover:ring-3 transition-all',
  secondary: 'bg-base text-base-content-100 bg-base-100 border-1 border-base-content-100/20 ring-0 ring-base-content-100/10 hover:ring-3 transition-all',
  accent: 'bg-accent text-accent-content ring-0 ring-accent/25 hover:ring-3 border-1 border-accent transition-all bg-radial-(--gradient-position) from-base-100/20 to-transparent to-50%',
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
const { elementX, elementY } = useMouseInElement(buttonRef)

const gradientPosition = computed(() => {
  // if (isOutside.value) return 'circle at 50% 100%'
  // const positionX = Math.min(Math.max(elementX.value, 0), elementWidth.value)
  // const positionY = Math.min(Math.max(elementY.value, 0), elementHeight.value)
  const positionX = elementX.value
  const positionY = elementY.value
  return `circle at ${positionX}px ${positionY}px`
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
    <Icon v-if="beforeIcon" class="my-1" :name="beforeIcon" />
    <span v-if="text">{{ text }}</span>
    <Icon v-if="afterIcon" class="my-1" :name="afterIcon" />
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
    <Icon v-if="beforeIcon" class="my-1" :name="beforeIcon" />
    <span v-if="text">{{ text }}</span>
    <Icon v-if="afterIcon" class="my-1" :name="afterIcon" />
  </button>
</template>
