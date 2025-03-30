<script setup lang="ts">
import { ref, watch } from 'vue'
import ToggleSelect from './ToggleSelect.vue'

const themeOptions = [
  { value: 'light', icon: 'light_mode', label: 'Modo claro' },
  { value: 'dark', icon: 'dark_mode', label: 'Modo escuro' },
  { value: 'system', icon: 'devices', label: 'Modo do sistema' },
]

const selectedTheme = ref('system')

watch(
  selectedTheme,
  (newTheme) => {
    if (newTheme === 'system') {
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
      document.documentElement.setAttribute('data-theme', prefersDark ? 'dark' : 'light')
    } else {
      document.documentElement.setAttribute('data-theme', newTheme)
    }
  },
  { immediate: true },
)
</script>

<template>
  <div class="theme-select">
    <ToggleSelect v-model="selectedTheme" :options="themeOptions" :aria-label="'Selecionar tema'" />
    <button aria-label="Tema aleatório">
      <span class="material-symbols-outlined"> shuffle </span>
    </button>
  </div>
</template>

<style scoped>
.theme-select {
  display: flex;
  background-color: var(--primary);
  align-items: center;
  border-radius: 8px;
}

button {
  background-color: transparent;
  color: var(--text-on-primary);
  border: none;
  height: 32px;
  width: 32px;
  padding: 4px;
  border-radius: 4px;
  margin: 4px;
}
</style>
