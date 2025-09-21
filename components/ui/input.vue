<script setup lang="ts">
withDefaults(defineProps<{
  type?: string
  label: string
  placeholder: string
  required?: boolean
  name: string
  id?: string
}>(), {
  type: 'text',
  required: false,
  id: useId(),
})

const value = defineModel<string>({ required: true })
</script>

<template>
  <div>
    <label :for="id" class="font-medium mb-1 after:content-['*'] after:text-secondary">{{ label }}</label>
    <input
      :id
      v-model="value"
      :type
      :name
      :placeholder
      class="
          transition-all bg-base-100
          hover:ring-3 hover:ring-base-content-100/10 hover:border-base-content-100/30
          focus-within:border-accent! focus-within:ring-3! focus-within:ring-accent/20!
          border-1 border-base-content-100/20 bg-base
          rounded-lg p-3 outline-none w-full flex flex-col items-end gap-2 mt-1
          placeholder:text-base-content-100/30 placeholder:font-medium
      "
    >
  </div>
</template>
