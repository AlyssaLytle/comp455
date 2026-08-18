<template>
  <div class="slidev-layout two-cols-layout">
    <div v-if="$frontmatter.kicker" class="kicker">{{ $frontmatter.kicker }}</div>
    <slot name="title" />
    <div class="cols">
      <div class="col left"><slot name="left" /></div>
      <div class="col right"><slot name="right" /></div>
    </div>
  </div>
</template>

<style scoped>
.two-cols-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: 5.2rem 7.3rem 4.2rem;
  background: var(--unc-ink);
}
.kicker {
  color: var(--unc-blue-pale);
}
.two-cols-layout :deep(h1){
  font-size: 2.9rem;
  font-weight: 700;
  color: var(--unc-blue-light);
  margin: 0 0 1.5rem;
}
.two-cols-layout :deep(h2) {
  font-size: 1.9rem;
  font-weight: 700;
  color: var(--unc-blue-pale);
  margin: 0 0 1.5rem;
}
.cols {
  display: flex;
  gap: 3.5rem;
  flex: 1;
  align-items: top;
}
.col {
  flex: 1;
  min-width: 0;
}
</style>
