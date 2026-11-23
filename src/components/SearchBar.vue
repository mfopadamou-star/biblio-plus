<script setup>
const model = defineModel({ type: String, default: '' })
</script>

<template>
  <form class="search" role="search" @submit.prevent>
    <label for="q" class="sr-only">Rechercher un livre</label>
    <input
      id="q"
      v-model="model"
      class="search__input"
      type="search"
      placeholder="Titre, auteur…"
      autocomplete="off"
    />
  </form>
</template>

<style scoped>
.search {
  width: 100%;
  max-width: 32rem;
}
.search__input {
  width: 100%;
  min-height: 44px;
  padding: var(--space-2) var(--space-4);
  border: 2px solid var(--color-primary);
  border-radius: var(--radius);
  background: var(--color-surface);
  color: var(--color-text);
  font: inherit;
}
.search__input::placeholder {
  color: var(--color-text);
  opacity: 0.6;
}
</style>