<script setup lang="ts">
import HeaderLogo from '../components/HeaderLogo.vue'
import ThemeSelect from './ThemeSelect.vue'
</script>

<template>
  <header class="outer">
    <div class="wrapper inner">
      <div class="logo-container">
        <HeaderLogo />
      </div>

      <nav class="hide-on-mobile">
        <RouterLink to="#">Trabalhos</RouterLink>
        <RouterLink to="#">Serviços</RouterLink>
        <RouterLink to="#">Sobre</RouterLink>
        <RouterLink to="#">Contato</RouterLink>
      </nav>

      <div class="actions">
        <ThemeSelect />
        <button class="primary hide-on-mobile">CURRÍCULO</button>
        <button class="secondary show-on-mobile">
          <span class="material-symbols-outlined"> menu </span>
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: space-between;
  flex: 1;
  align-items: center;
  padding: 1rem 0;
}

nav a {
  color: var(--text-medium);
  text-decoration: none;
  margin: 0.5rem;
}

nav a :hover {
  color: var(--text-strong);
  text-decoration: underline;
}

.logo-container {
  display: flex;
  align-items: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
  height: 24px;
}

.actions {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
</style>
