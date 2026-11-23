<script setup>
import { useSlots } from 'vue'
const slots = useSlots()
</script>

<template>
  <article class="card">
    <header v-if="slots.header" class="card__header">
      <slot name="header" />
    </header>

    <div class="card__body">
      <slot />
    </div>

    <footer v-if="slots.footer" class="card__footer">
      <slot name="footer" />
    </footer>
  </article>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  overflow: hidden;
  background: var(--color-surface);
  border-radius: var(--radius);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
.card__header,
.card__footer { padding: var(--space-4); }
.card__body   { flex: 1; padding: var(--space-4); }
.card__footer { border-top: 1px solid rgba(128, 128, 128, 0.3); }
</style>