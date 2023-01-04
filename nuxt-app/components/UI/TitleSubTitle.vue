<template>
  <div class="title">
    <h1 class="main-title">{{ title }}</h1>
    <p class="sub-title">{{ subTitle }}</p>
  </div>
</template>
<script setup>
const props = defineProps({
  title: String,
  subTitle: String,
});
</script>
<style scoped>
.title {
  text-align: center;
}
.main-title {
  color: #1166bc;
  font-size: 40px;
}
.sub-title {
  color: gray;
  font-size: 20px;
}
@media screen and (max-width: 576px) {
  .sub-title {
    font-size: 15px;
  }
  .main-title {
    font-size: 25px;
  }
}
</style>
