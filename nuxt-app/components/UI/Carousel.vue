<template>
  <div class="carousel">
    <button @click="prevImageToggle">prev</button>

    <div class="carousel-images col-9">
      <img class="prev-image" width="300" height="300" v-bind:src="prevImage" />
      <img
        class="current-image"
        width="300"
        height="300"
        v-bind:src="currentImage"
      />
      <img class="next-image" width="300" height="300" v-bind:src="nextImage" />
    </div>
    <button @click="nextImageToggle">next</button>
  </div>
</template>

<script setup>
const currentIndex = ref(0);
const images = ref([
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
]);
const prevImage = computed(() => images.value[currentIndex.value - 1]);
const currentImage = computed(() => images.value[currentIndex.value]);
const nextImage = computed(() => images.value[currentIndex.value + 1]);

const nextImageToggle = () => {
  currentIndex.value < images.value.length ? currentIndex.value++ : 0;
};

const prevImageToggle = () => {
  currentIndex.value--;
};

watch(
  () => images.value,
  () => {
    currentIndex.value = 0;
  }
);
</script>

<style scoped>
.carousel {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.carousel-images {
  display: flex;
  transition: all 0.3s ease;
  justify-content: space-between;
}
.prev-image,
.next-image {
  filter: blur(4px);
  transition: all 0.3s ease;
}
</style>
