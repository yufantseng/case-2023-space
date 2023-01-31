<template>
  <svg width="32" height="32" viewBox="0 0 32 32" fill="none">
    <path
      d="M9.33398 17.3334L16.0007 24L22.6673 17.3334"
      stroke="#"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="first"
    />
    <path
      d="M9.33398 8L16.0007 14.6667L22.6673 8"
      stroke="#"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="second"
    />
  </svg>
</template>

<style lang="scss" scoped>
.first,
.second {
  animation: scrollDownArrow 1.2s infinite ease-in-out;
  stroke: var(--color-text-white);
}
.first {
  animation-delay: 0.2s;
}
@keyframes scrollDownArrow {
  0% {
    stroke-width: 0.1rem;
    opacity: 0.7;
  }
  100% {
    stroke-width: 0.125rem;
    opacity: 1;
  }
}
</style>
