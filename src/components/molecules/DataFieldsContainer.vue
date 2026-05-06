<script setup>
import DataField from '../atoms/DataField.vue';
</script>

<template>
  <ul class="data-field__list">
    <DataField label="Day" placeholder="DD"></DataField>
    <DataField label="Month" placeholder="MM"></DataField>
    <DataField label="Year" placeholder="YYYY"></DataField>
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