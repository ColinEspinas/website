<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: '',
})
</script>

<template>
  <section class="flex flex-col gap-4">
    <h2 id="contact" class="text-4xl font-bold text-base-content-100">
      Get in touch
    </h2>
    <p class="text-base-content-200 font-medium">
      I am open to conversations, if you have any question about my content, my work or simply want to chat with me you can contact me on various social medias such as Twitter, LinkedIn, GitHub or simply use the form below.
    </p>

    <form class="mt-6">
      <div class="flex flex-col gap-2">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-2">
          <UiInput v-model="form.name" class="col-span-1" name="name" label="Name" placeholder="Your name" required />
          <UiInput v-model="form.email" class="col-span-2" name="email" label="Email" type="email" placeholder="Your email" required />
        </div>
        <UiTextarea v-model="form.message" name="message" label="Message" placeholder="Your message" required />
        <UiButton before-icon="ph:paper-plane-tilt" text="Send message" variant="accent" class="w-fit" />
      </div>
    </form>
  </section>
</template>
