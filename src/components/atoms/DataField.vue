<script setup lang="ts">
defineProps<{
  label: string;
  placeholder?: string;
}>();
</script>

<template>
  <li class="data-field">
    <p class="data-field__label">{{ label }}</p>
    <input type="text" :placeholder="placeholder" class="data-field__value">
  </li>
</template>

<style>
.data-field {
  display: flex;
  flex-direction: column;
}

.data-field__label {
  margin-bottom: 8px;
  text-transform: uppercase;
  font: var(--text-preset-6-bold);
  letter-spacing: var(--text-preset-6-bold-letter-spacing);
  color: var(--color-grey-500);
}

.data-field__value {
  width: 88px;
  height: 46px;
  padding: 8px 16px;
  border-radius: 8px;
  border: 1px solid var(--color-grey-200);
}

.data-field__value::placeholder {
  font: var(--text-preset-4);
  letter-spacing: var(--text-preset-2-letter-spacing);
  color: var(--color-grey-500);
}

@media (min-width: 768px) {
  .data-field__label {
    font: var(--text-preset-5-bold);
    letter-spacing: var(--text-preset-5-bold-letter-spacing);
  }

  .data-field__value {
    width: 170px;
    height: 64px;
    padding: 8px 24px;
  }

  .data-field__value::placeholder {
    font: var(--text-preset-3);
    letter-spacing: var(--text-preset-3-letter-spacing);
  }
}
</style>
