<script setup>
import { reactive, computed, ref } from 'vue'

// État du formulaire
const form = reactive({ name: '', email: '', message: '' })

// Champs déjà visités (pour n'afficher les erreurs qu'après)
const touched = reactive({ name: false, email: false, message: false })

// Envoi réussi ou non
const sent = ref(false)

// Erreurs recalculées automatiquement à chaque saisie
const errors = computed(() => ({
  name: form.name.trim().length < 2 ? 'Votre nom est requis.' : '',
  email: /^\S+@\S+\.\S+$/.test(form.email) ? '' : 'Adresse e-mail invalide.',
  message: form.message.trim().length < 10 ? '10 caractères minimum.' : '',
}))

// Vrai si aucun champ n'a d'erreur
const isValid = computed(() => Object.values(errors.value).every(e => !e))

function submit() {
  // On marque tous les champs comme visités pour afficher toutes les erreurs
  Object.keys(touched).forEach(k => (touched[k] = true))
  if (!isValid.value) return
  sent.value = true // simulation : aucun back-end dans ce projet
}
</script>

<template>
  <h1>Contact</h1>
  <p v-if="sent" role="status">Merci, votre message a bien été envoyé.</p>
  <form v-else novalidate @submit.prevent="submit">
    <div class="field">
      <label for="name">Nom</label>
      <input id="name" v-model="form.name" @blur="touched.name = true"
             :aria-invalid="touched.name && !!errors.name"
             aria-describedby="name-err" />
      <p id="name-err" class="field__error"
         v-if="touched.name && errors.name">{{ errors.name }}</p>
    </div>
    <!-- idem pour email et message -->
    <BaseButton type="submit">Envoyer</BaseButton>
  </form>
</template>
