<script setup>
import { RouterLink } from 'vue-router'

defineProps({
  variant: { type: String, default: 'primary' }, // primary | ghost
  to: { type: [String, Object], default: null }, // lien interne si renseigné
  type: { type: String, default: 'button' },     // button | submit (si pas de lien)
})
</script>

<template>
  <component
    :is="to ? RouterLink : 'button'"
    :to="to || undefined"
    :type="to ? undefined : type"
    :class="['btn', 'btn--' + variant]"
  >
    <slot />
  </component>
</template>

<style scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 44px;
  padding: var(--space-2) var(--space-6);
  border: 2px solid var(--color-primary);
  border-radius: var(--radius);
  font: inherit;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  transition: background-color 0.2s ease, color 0.2s ease;
}

.btn--primary {
  background: var(--color-primary);
  color: var(--color-primary-contrast);
}
.btn--primary:hover {
  background: var(--color-text);
  border-color: var(--color-text);
}

.btn--ghost {
  background: transparent;
  color: var(--color-primary);
}
.btn--ghost:hover {
  background: var(--color-primary);
  color: var(--color-primary-contrast);
}

.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>