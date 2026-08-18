<template>
  <div class="slidev-layout cover-layout">
    <img v-if="$slidev.configs.logo" class="cover-logo" :src="$slidev.configs.logo" alt="logo" />
    <div v-if="$frontmatter.kicker" class="kicker cover-kicker">{{ $frontmatter.kicker }}</div>
    <slot />
  </div>
</template>

<style scoped>
.cover-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 5.7rem;
  background: var(--unc-navy);
  color: #fff;
}
.cover-logo {
  width: 110px;
  height: auto;
  border-radius: 8px;
  margin-bottom: 2.5rem;
}
.cover-kicker {
  color: var(--unc-blue-light);
}
.cover-layout :deep(h1) {
  font-size: 4.2rem;
  font-weight: 700;
  color: #fff;
  margin: 0 0 1rem;
  line-height: 1.05;
}
.cover-layout :deep(p) {
  font-size: 1.7rem;
  color: var(--unc-blue-pale);
  font-weight: 400;
  margin: 0;
}
</style>
