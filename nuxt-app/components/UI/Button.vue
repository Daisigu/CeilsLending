<template>
  <button type="button" class="btn">
    <slot />
  </button>
</template>

<style scoped>
.btn {
  padding: 0.7rem;
  border-radius: 0.5rem;
  border: 1px solid lightgray;
  background-color: #1a7fe4;
  color: white;
  cursor: pointer;
}
.btn:hover {
  transition: all 0.3s ease;
  background-color: #1d8eff;
}
</style>
