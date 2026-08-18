<template>
  <div class="slidev-layout cover-layout">
    <div v-if="$frontmatter.kicker" class="kicker cover-kicker">{{ $frontmatter.kicker }}</div>
    <slot />
  </div>
</template>

<style scoped>
.cover-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  padding: 24px 24px;
  background: var(--unc-ink);
  color: #fff;
  box-sizing:border-box;
  font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;

}
.cover-kicker {
  color: var(--unc-blue);
  font-size: 24px;
  letter-spacing: 4px;
  font-weight: 700;
  text-transform:uppercase;
  /* margin-bottom:28px; */
}
.cover-layout :deep(h1) {
  font-size: 84px;
  font-weight: 700;
  color: var(--unc-paper);
  margin: 0 0 24px;
  line-height: 1.05;
}
.cover-layout :deep(h2) {
  font-size: 36px;
  font-weight: 700;
  color: var(--unc-blue-light);
  margin: 0 0 1rem;
  line-height: 1.05;
}
.cover-layout :deep(p) {
  font-size: 24px;
  color: var(--unc-blue-pale);
  font-weight: 400;
}
</style>
