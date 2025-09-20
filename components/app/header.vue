<script setup lang="ts">
const { width } = useWindowSize()
</script>

<template>
  <header class="flex flex-col gap-6 my-28">
    <AppAvailability />
    <h2 class="text-5xl font-bold">
      Hello,
      <br>
      I'm
      <template v-if="width <= 480">
        <UiWavyText>Colin</UiWavyText>&nbsp;
        <UiWavyText>Espinas</UiWavyText>
      </template>
      <template v-else>
        <UiWavyText>Colin Espinas</UiWavyText>
      </template>
    </h2>
    <h1 class="text-2xl font-semibold text-base-content-200">
      A developer focused on crafting tools and experiences to make the web more open, accessible and beautiful.
    </h1>
    <div class="flex flex-col sm:flex-row gap-4">
      <UiButton text="Start a conversation" variant="accent" class="w-fit" />
      <div class="flex flex-row gap-2">
        <UiButton
          before-icon="ph:github-logo"
          variant="secondary"
          shape="rounded"
          to="https://github.com/ColinEspinas"
          target="_blank"
        />
        <UiButton
          after-icon="ph:x-logo"
          variant="secondary"
          shape="rounded"
          to="https://x.com/call_innn"
          target="_blank"
        />
        <UiButton
          after-icon="ph:linkedin-logo"
          variant="secondary"
          shape="rounded"
          to="https://www.linkedin.com/in/colin-espinas/"
          target="_blank"
        />
      </div>
    </div>
  </header>
</template>
