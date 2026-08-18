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
  padding: 5.2rem 7.3rem 4.2rem;
  background: var(--unc-paper);
  color: var(--unc-ink);
}
.kicker {
  color: var(--unc-blue);
}
.default-layout :deep(h1),
.default-layout :deep(h2) {
  font-size: 2.9rem;
  font-weight: 700;
  color: var(--unc-navy);
  margin: 0 0 2rem;
}
.default-layout :deep(p),
.default-layout :deep(li) {
  font-size: 1.65rem;
  line-height: 1.5;
  color: var(--unc-ink);
}
.default-layout :deep(code) {
  background: var(--unc-blue-tint);
  padding: 0.1em 0.45em;
  border-radius: 6px;
  color: var(--unc-navy);
}
</style>
