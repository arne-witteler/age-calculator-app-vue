<script setup lang="ts">
defineProps<{
  label: string;
  placeholder?: string;
  errorMessage?: string;
  maxLength?: number;
}>();

const model = defineModel<string>({ default: '' });

const handleInput = (event: Event) => {
  const input = event.target as HTMLInputElement;
  const sanitizedValue = input.value.replace(/\D/g, '');

  input.value = sanitizedValue;
  model.value = sanitizedValue;
};
</script>

<template>
  <li class="data-field">
    <p class="data-field__label" :class="{ 'data-field--error': errorMessage }">{{ label }}</p>
    <input :value="model" type="text" inputmode="numeric" pattern="[0-9]*" :maxlength="maxLength"
      :placeholder="placeholder" class="data-field__value" @input="handleInput"
      :class="{ 'data-field--error': errorMessage }">
    <p v-if="errorMessage" class="data-field__error-message">
      {{ errorMessage }}
    </p>
  </li>
</template>

<style>
.data-field {
  display: flex;
  flex-direction: column;
  position: relative;
}

.data-field__label {
  margin-bottom: 8px;
  text-transform: uppercase;
  font: var(--text-preset-6-bold);
  letter-spacing: var(--text-preset-6-bold-letter-spacing);
  color: var(--color-grey-500);
}

.data-field__label.data-field--error {
  color: var(--color-red-400);
}

.data-field__value {
  font: var(--text-preset-4);
  letter-spacing: var(--text-preset-4-letter-spacing);
  width: 88px;
  height: 46px;
  padding: 8px 16px;
  border-radius: 8px;
  border: 1px solid var(--color-grey-200);
}

.data-field__value.data-field--error {
  border-color: var(--color-red-400);
}

.data-field__value::placeholder {
  font: var(--text-preset-4);
  letter-spacing: var(--text-preset-4-letter-spacing);
  color: var(--color-grey-500);
}

.data-field__error-message {
  position: absolute;
  top: 80px;
  left: 0;
  max-width: 88px;
  font: var(--text-preset-6-italic);
  letter-spacing: var(--text-preset-6-italic-letter-spacing);
  color: var(--color-red-400);
}

@media (min-width: 768px) {
  .data-field__label {
    font: var(--text-preset-5-bold);
    letter-spacing: var(--text-preset-5-bold-letter-spacing);
  }

  .data-field__value {
    font: var(--text-preset-3);
    letter-spacing: var(--text-preset-3-letter-spacing);
    width: 170px;
    height: 64px;
    padding: 8px 24px;
  }

  .data-field__value::placeholder {
    font: var(--text-preset-3);
    letter-spacing: var(--text-preset-3-letter-spacing);
  }

  .data-field__error-message {
    top: 101px;
    max-width: 170px;
    font: var(--text-preset-5-italic);
    letter-spacing: var(--text-preset-5-italic-letter-spacing);
  }
}
</style>
