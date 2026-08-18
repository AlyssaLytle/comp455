<template>
  <div class="slidev-layout statement-layout">
    <div v-if="$frontmatter.kicker" class="kicker statement-kicker">{{ $frontmatter.kicker }}</div>
    <slot />
  </div>
</template>

<style scoped>
.statement-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 5.2rem 7.3rem;
  background: var(--unc-navy);
  color: #fff;
}
.statement-kicker {
  color: var(--unc-blue-light);
}
.statement-layout :deep(h1),
.statement-layout :deep(h2) {
  font-size: 3.4rem;
  font-weight: 700;
  color: #fff;
  max-width: 1400px;
  margin: 0 0 2rem;
}
.statement-layout :deep(p) {
  font-size: 1.8rem;
  color: var(--unc-blue-pale);
  line-height: 1.6;
  max-width: 1300px;
}
</style>
