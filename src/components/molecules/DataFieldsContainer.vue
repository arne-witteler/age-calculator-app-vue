<script setup lang="ts">
import DataField from '../atoms/DataField.vue';

defineProps<{
  errors: {
    day: string;
    month: string;
    year: string;
  }
}>();

const model = defineModel<{
  day: string;
  month: string;
  year: string;
}>({
  default: {
    day: '',
    month: '',
    year: '',
  },
});
</script>

<template>
  <ul class="data-field__list">
    <DataField v-model="model.day" label="Day" placeholder="DD" :max-length="2" :error-message="errors.day"></DataField>
    <DataField v-model="model.month" label="Month" placeholder="MM" :max-length="2" :error-message="errors.month"></DataField>
    <DataField v-model="model.year" label="Year" placeholder="YYYY" :max-length="4" :error-message="errors.year"></DataField>
  </ul>
</template>

<style>
.data-field__list {
  display: flex;
  justify-content: space-between;
  list-style: none;
}

@media (min-width: 768px) {
  .data-field__list {
    justify-content: flex-start;
    gap: 24px;
  }
}
</style>
