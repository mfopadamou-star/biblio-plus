<script setup>
import { ref, computed, onMounted } from 'vue'
import { useBooks } from '@/composables/useBooks'
import SearchBar from '@/components/SearchBar.vue'
import BookList from '@/components/BookList.vue'

const { books, loading, error, load } = useBooks()
const query = ref('')
const featured = computed(() =>
  books.value
    .filter(b => b.title.toLowerCase().includes(query.value.toLowerCase()))
    .slice(0, 8))

onMounted(load)
</script>
 
<template>
  <section class="hero">
    <h1>Bienvenue à la bibliothèque</h1>
    <SearchBar v-model="query" />
  </section>
  <section aria-labelledby="coeur">
  <h2 id="coeur">Coups de cœur</h2>
  <p v-if="loading" role="status">Chargement…</p>
  <div v-else-if="error" role="alert">
    <p>{{ error }}</p>
    <button type="button" @click="load">Réessayer</button>
  </div>
  <BookList v-else :books="featured" />
</section>
</template>
