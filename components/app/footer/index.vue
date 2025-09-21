<script setup lang="ts">
const { y } = useWindowScroll({ behavior: 'smooth' })
</script>

<template>
  <footer class="relative mt-30">
    <div class="absolute -z-50 bottom-full left-0 w-full h-[240px] border-b border-base-200 mask-radial-at-bottom mask-radial-[50%_50%] mask-radial-from-10% bg-[linear-gradient(to_right,var(--color-base-200)_1px,transparent_1px),linear-gradient(to_bottom,var(--color-base-200)_1px,transparent_1px)] bg-[size:24px_24px]" />
    <div class="flex flex-col max-w-[500px] md:max-w-[640px] mx-auto px-10 md:px-0 py-10">
      <nav class="flex flex-col-reverse gap-10 md:flex-row justify-between ">
        <div class="flex flex-col md:flex-row gap-10">
          <div class="flex flex-col gap-2">
            <AppFooterLink
              :to="$localePath('index')"
              text="Home"
            />
            <AppFooterLink
              :to="$localePath('about')"
              text="About"
            />
            <AppFooterLink
              :to="$localePath('contact')"
              text="Contact"
            />
          </div>
          <div class="flex flex-col gap-2">
            <AppFooterLink
              to="https://github.com/ColinEspinas"
              text="Github"
              external
              target="_blank"
            />
            <AppFooterLink
              to="https://x.com/call_innn"
              text="X (Twitter)"
              external
              target="_blank"
            />
            <AppFooterLink
              to="https://www.linkedin.com/in/colin-espinas/"
              text="LinkedIn"
              external
              target="_blank"
            />
          </div>
          <div class="flex flex-col gap-2">
            <AppFooterLink
              to="https://codepen.io/Call_in"
              text="Codepen"
              external
              target="_blank"
            />
            <AppFooterLink
              to="https://github.com/ColinEspinas/website"
              text="Source code"
              external
              target="_blank"
            />
          </div>
        </div>
        <div class="flex flex-col">
          <UiButton
            variant="secondary"
            size="sm"
            before-icon="ph:arrow-up"
            text="Go back up"
            class="w-fit"
            @click="y = 0"
          />
        </div>
      </nav>
      <div class="text-sm text-base-content-200 font-semibold mt-10">
        <p>All content © 2025 Colin Espinas. All Rights reserved.</p>
        <p>Source code is available under the MIT License.</p>
      </div>
    </div>
  </footer>
</template>
