<script setup>
import Button from '../atoms/Button.vue';
import AgeContainer from '../molecules/AgeContainer.vue';
import DataFieldsContainer from '../molecules/DataFieldsContainer.vue';

import { ref } from 'vue';

const dateOfBirth = ref({
  day: '',
  month: '',
  year: '',
});

const errors = ref({
  day: '',
  month: '',
  year: '',
});

const age = ref({
  years: '--',
  months: '--',
  days: '--',
});

const isValidDate = (day, month, year) => {
  const date = new Date();
  date.setFullYear(year, month - 1, day);
  date.setHours(0, 0, 0, 0);

  return (
    date.getFullYear() === year &&
    date.getMonth() === month - 1 &&
    date.getDate() === day
  );
};

const isFourDigitYear = (year) => /^\d{4}$/.test(year);

const calculateAge = (day, month, year) => {
  const today = new Date();
  let years = today.getFullYear() - year;
  let months = today.getMonth() - (month - 1);
  let days = today.getDate() - day;

  if (days < 0) {
    months -= 1;
    days += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
  }

  if (months < 0) {
    years -= 1;
    months += 12;
  }

  age.value = {
    years,
    months,
    days,
  };
};

const validateDateOfBirth = () => {
  const day = Number(dateOfBirth.value.day);
  const month = Number(dateOfBirth.value.month);
  const year = Number(dateOfBirth.value.year);
  const today = new Date();
  const selectedDate = new Date(year, month - 1, day);

  errors.value = {
    day: '',
    month: '',
    year: '',
  };

  if (!dateOfBirth.value.day) {
    errors.value.day = 'This field is required';
  } else if (!Number.isInteger(day) || day < 1 || day > 31) {
    errors.value.day = 'Must be a valid day';
  }

  if (!dateOfBirth.value.month) {
    errors.value.month = 'This field is required';
  } else if (!Number.isInteger(month) || month < 1 || month > 12) {
    errors.value.month = 'Must be a valid month';
  }

  if (!dateOfBirth.value.year) {
    errors.value.year = 'This field is required';
  } else if (!isFourDigitYear(dateOfBirth.value.year) || year < 1) {
    errors.value.year = 'Must be a valid year';
  } else if (!Number.isInteger(year) || selectedDate > today) {
    errors.value.year = 'Must be in the past';
  }

  if (!errors.value.day && !errors.value.month && !errors.value.year && !isValidDate(day, month, year)) {
    errors.value.day = 'Must be a valid date';
  }

  if (errors.value.day || errors.value.month || errors.value.year) {
    age.value = {
      years: '--',
      months: '--',
      days: '--',
    };

    return;
  }

  calculateAge(day, month, year);
};

</script>

<template>
  <div class="card">
    <DataFieldsContainer v-model="dateOfBirth" :errors="errors"></DataFieldsContainer>
    <div class="card__button">
      <Button @click="validateDateOfBirth"></Button>
    </div>
    <AgeContainer :years="age.years" :months="age.months" :days="age.days"></AgeContainer>
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
