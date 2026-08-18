<template>
  <div class="slidev-layout section-layout">
    <div v-if="$frontmatter.index" class="section-index">{{ $frontmatter.index }}</div>
    <slot />
  </div>
</template>

<style scoped>
.section-layout {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 7.3rem;
  background: var(--unc-navy);
}
.section-index {
  font-size: 11.5rem;
  font-weight: 700;
  color: var(--unc-navy-soft);
  line-height: 1;
  margin-bottom: 0.4rem;
}
.section-layout :deep(h1),
.section-layout :deep(h2) {
  font-size: 4rem;
  font-weight: 700;
  color: #fff;
  margin: 0;
}
</style>
