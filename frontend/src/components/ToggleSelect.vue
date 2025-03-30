<script setup lang="ts">
interface Option {
  value: string
  icon: string
  label: string
}

const props = defineProps<{
  options: Option[]
  modelValue: string
}>()

const emit = defineEmits(['update:modelValue'])

const selectOption = (value: string) => {
  emit('update:modelValue', value)
}
</script>

<template>
  <div class="toggle-select">
    <button
      v-for="option in options"
      :key="option.value"
      :class="{ active: option.value === props.modelValue }"
      :aria-label="option.label"
      @click="selectOption(option.value)"
    >
      <span class="material-symbols-outlined"> {{ option.icon }} </span>
    </button>
  </div>
</template>

<style scoped>
.toggle-select {
  background-color: var(--background);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px;
  border: 1px solid var(--primary);
  border-radius: 8px;

}

button {
  background-color: transparent;
  color: var(--text-weak);
  border: none;
  height: 32px;
  width: 32px;
  padding: 4px;
  border-radius: 4px;
  justify-content: center;
}

button :hover {
  cursor: pointer;
  color: var(--text-strong);
}

button.active {
  background-color: var(--primary);
  color: var(--text-on-primary);
}

button.active :hover {
  background-color: var(--primary);
  color: var(--text-on-primary);
}

</style>
