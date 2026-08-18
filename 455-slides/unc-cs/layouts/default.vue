<template>
  <div class="slidev-layout default-layout">
    <div v-if="$frontmatter.kicker" class="kicker">{{ $frontmatter.kicker }}</div>
    <slot />
  </div>
</template>

<style scoped>
.default-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: 20px 20px 20px;
  background: var(--unc-ink);
  color: var(--unc-paper);
}
.kicker {
  color: var(--unc-blue-pale);
}
.default-layout :deep(h1){
  font-size: 2.9rem;
  font-weight: 700;
  color: var(--unc-blue-light);
  margin: 0 0 1.5rem;
}
.default-layout :deep(h2) {
  font-size: 1.9rem;
  font-weight: 700;
  color: var(--unc-blue-pale);
  margin: 0 0 1.5rem;
}
.default-layout :deep(p),
.default-layout :deep(li) {
  font-size: 1.65rem;
  line-height: 1.75;
  color: var(--unc-paper);
}
.default-layout :deep(code) {
  background: var(--unc-blue-tint);
  padding: 0.1em 0.45em;
  border-radius: 6px;
  color: var(--unc-navy);
}
</style>
