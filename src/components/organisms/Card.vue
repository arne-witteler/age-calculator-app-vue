<script setup>
import Button from '../atoms/Button.vue';
import AgeContainer from '../molecules/AgeContainer.vue';
import DataFieldsContainer from '../molecules/DataFieldsContainer.vue';
</script>

<template>
  <div class="card">
    <DataFieldsContainer></DataFieldsContainer>
    <div class="card__button">
      <Button></Button>
    </div>
    <AgeContainer></AgeContainer>
  </div>
</template>

<style>
.card {
  max-width: 343px;
  padding: 48px 24px 24px 24px;
  background-color: var(--color-white);
  border-radius: 24px 24px 100px 24px;
}

.card ul {
  display: flex;
  gap: 16px;
  list-style: none;
  margin-bottom: 32px;
}

.card__button {
  display: flex;
  justify-content: center;
  margin: 32px 0;
}

@media (min-width: 768px) {
  .card {
    max-width: 686px;
    padding: 56px 48px 24px 48px;
  }

  .card ul {
    gap: 24px;
    margin-bottom: 48px;
  }
}

@media (min-width: 1024px) {
  .card {
    max-width: none;
    width: 840px;

  }
}
</style>
