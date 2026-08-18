<template>
  <div class="slidev-layout end-layout">
    <img v-if="$slidev.configs.logo" class="end-logo" :src="$slidev.configs.logo" alt="logo" />
    <slot />
  </div>
</template>

<style scoped>
.end-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding: 0 7.3rem;
  background: var(--unc-navy);
  color: #fff;
}
.end-logo {
  width: 90px;
  height: auto;
  border-radius: 8px;
  margin-bottom: 2.5rem;
}
.end-layout :deep(h1) {
  font-size: 4.2rem;
  font-weight: 700;
  color: #fff;
  margin: 0 0 1.2rem;
}
.end-layout :deep(p) {
  font-size: 1.7rem;
  color: var(--unc-blue-pale);
}
</style>
