<template>
  <span class="relative after:content-[''] after:absolute after:top-0 after:left-0 after:w-full after:-z-10 after:bg-repeat-x after:bg-bottom wavy-bg">
    <slot />
  </span>
</template>

<style scoped>
.wavy-bg::after {
  height: calc(100% + 3px);
  background-image: url('data:image/svg+xml;utf8,<svg viewBox="0 0 31 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M0.942398 13C8.428 13 8.428 3 15.896 3C23.3818 3 23.3818 13 30.8497 13" stroke="%2347DCFF" stroke-width="6" stroke-miterlimit="10" stroke-linecap="square"/></svg>');
  background-size: 25px auto;
  animation: wavy 1000ms linear infinite;
}

@keyframes wavy {
  from {
    background-position-x: 0;
  }
  to {
    background-position-x: 25px;
  }
}
</style>
