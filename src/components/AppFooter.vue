<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <footer class="app-footer">
    <div class="app-footer__inner">
      <section class="app-footer__block" aria-labelledby="footer-nom">
        <h2 id="footer-nom" class="app-footer__title">Bibliothèque municipale</h2>
        <p>12 rue des Livres, 75000 Ville</p>
      </section>

      <section class="app-footer__block" aria-labelledby="footer-horaires">
        <h2 id="footer-horaires" class="app-footer__title">Horaires</h2>
        <ul class="app-footer__list">
          <li>Mardi au vendredi : 10 h – 18 h</li>
          <li>Samedi : 10 h – 17 h</li>
          <li>Dimanche et lundi : fermé</li>
        </ul>
      </section>

      <section class="app-footer__block" aria-labelledby="footer-contact">
        <h2 id="footer-contact" class="app-footer__title">Contact</h2>
        <p>
          <RouterLink class="app-footer__link" to="/contact">
            Nous écrire
          </RouterLink>
        </p>
        <p>
          <a class="app-footer__link" href="mailto:contact@biblio-plus.example">
            contact@biblio-plus.example
          </a>
        </p>
      </section>
    </div>

    <p class="app-footer__legal">© 2026 Biblio+ — Projet pédagogique</p>
  </footer>
</template>

<style scoped>
.app-footer {
  margin-top: var(--space-6);
  padding: var(--space-6);
  background: var(--color-text);
  color: var(--color-primary-contrast);
}
.app-footer__inner {
  display: grid;
  gap: var(--space-6);
  grid-template-columns: repeat(auto-fit, minmax(14rem, 1fr));
}
.app-footer__title {
  margin: 0 0 var(--space-2);
  font-size: var(--fs-300);
}
.app-footer__list {
  margin: 0;
  padding: 0;
  list-style: none;
}
.app-footer__link {
  color: inherit;
  text-decoration: underline;
}
.app-footer__legal {
  margin: var(--space-6) 0 0;
  font-size: 0.875rem;
  opacity: 0.8;
}
</style>