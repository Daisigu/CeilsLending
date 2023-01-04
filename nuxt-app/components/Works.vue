<template>
  <section id="works" class="works">
    <div class="container">
      <UITitleSubTitle
        title="Фотографии наших работ"
        sub-title="Посмотрите фотографии недавно выполненных нами работ"
      />
      <carousel :items-to-show="3">
        <slide v-for="slide in images" :key="slide">
          <img @click="fullImgSrc" width="250" height="250" :src="slide" alt="" />
        </slide>

        <template #addons>
          <navigation />
          <pagination />
        </template>
      </carousel>
    </div>
  </section>
</template>

<script setup>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";
const fullImgSrc = ref(null);
const images = ref([
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
]);
</script>

<style scoped>
.works {
  padding-top: 4rem;
  padding-bottom: 4rem;
  background-color: #f3f6f9;
}
.carousel {
  margin-top: 2rem;
}
</style>
