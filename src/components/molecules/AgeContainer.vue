<script setup>
</script>

<template>
  <ul class="age-calculation__list">
    <li class="age-calculation__item">
      <p class="age-calculation__value">--</p>
      <p class="age-calculation__label">years</p>
    </li>
    <li class="age-calculation__item">
      <p class="age-calculation__value">--</p>
      <p class="age-calculation__label">months</p>
    </li>
    <li class="age-calculation__item">
      <p class="age-calculation__value">--</p>
      <p class="age-calculation__label">days</p>
    </li>
  </ul>
</template>

<style>
.age-calculation__list {
  display: flex;
  flex-direction: column;
  list-style: none;
  margin-bottom: 32px;
}

.age-calculation__item {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 8px;
}

.age-calculation__value {
  font: var(--text-preset-2);
  letter-spacing: var(--text-preset-2-letter-spacing);
  color: var(--color-purple-500);
}

.age-calculation__label {
  font: var(--text-preset-2);
  letter-spacing: var(--text-preset-2-letter-spacing);
}

@media (min-width: 768px) {

  .age-calculation__value,
  .age-calculation__label {
    font: var(--text-preset-1);
    letter-spacing: var(--text-preset-1-letter-spacing);
  }
}
</style>