<script setup>
</script>

<template>
  <div class="divider">
    <button class="button">
      <img class="button__icon" src="../../assets/images/icon-arrow.svg" alt="Calculate age" />
    </button>
  </div>
</template>

<style>
.divider {
  display: flex;
  align-items: center;
  width: 100%;
}

.divider::before,
.divider::after {
  content: "";
  flex: 1;
  height: 1px;
  background-color: var(--color-grey-200);
}

.button {
  background-color: var(--color-purple-500);
  border-radius: 50%;
  border: none;
  width: 64px;
  height: 64px;
}

.button:active {
  background-color: var(--color-black);
}

.button__icon {
  width: 24px;
  height: 24px;
}


@media (min-width: 768px) {
  .button {
    width: 96px;
    height: 96px;
  }

  .button__icon {
    width: 44px;
    height: 44px;
  }
}

@media (min-width: 1024px) {
  .divider:after {
    flex: 0;
  }
}
</style>