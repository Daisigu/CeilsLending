<template>
  <section id="works" class="works">
    <div class="container">
      <UITitleSubTitle
        title="Фотографии наших работ"
        sub-title="Посмотрите фотографии недавно выполненных нами работ"
      />
      <carousel
        :items-to-show="4"
        :wrapAround="true"
        :breakpoints="breakpoints"
      >
        <slide v-for="slide in images" :key="slide">
          <img
          class="carousel-img"
            @click="
              fullImgSrc = slide;
              imgModal = true;
            "
            width="250"
            height="250"
            :src="slide"
            alt=""
          />
        </slide>

        <template #addons>
          <navigation />
          <pagination />
        </template>
      </carousel>
    </div>
    <UI-Modal :image-modal="true" :open="imgModal" @close="imgModal = false">
      <template #main>
        <img style="width: 100%; user-select: none" :src="fullImgSrc" alt="" />
      </template>
    </UI-Modal>
  </section>
</template>

<script setup>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";
const fullImgSrc = ref(null);
const imgModal = ref(false);
const images = ref([
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-12-08_53_47.jpeg",
  "https://optstroy24.ru/images/gallery/photo_2022-05-17-16_03_44.jpeg",
  "https://optstroy24.ru/images/gallery/balkony-int%20(3).jpg",
  "https://sun9-48.userapi.com/impg/PZX0P9wiYNLBQRAagKGGAvDceeW-4Zgv6SqyZQ/j3TBEEdcUUI.jpg?size=480x270&quality=95&sign=af80054cbe9c4f10faa9905616b96d60&type=album",
  "https://sun1.sibirix.userapi.com/impg/ZxsUuDvpM9UFYVN_JdjXyBK9iCMgtYsg4ozrvA/Xt84ulgoFRE.jpg?size=1090x1036&quality=96&sign=d252ab4d6efd97eacd34ce0e62e3f8ab&type=album",
]);
const breakpoints = ref({
  300: {
    itemsToShow: 1,
    snapAlign: "center",
  },
  400: {
    itemsToShow: 1.5,
    snapAlign: "center",
  },
  576: {
    itemsToShow: 2,
    snapAlign: "center",
  },
  700: {
    itemsToShow: 2,
    snapAlign: "center",
  },
  // 1024 and up
  1024: {
    itemsToShow: 3,
    snapAlign: "start",
  },
   1400: {
    itemsToShow: 4,
    snapAlign: "start",
  },
 
});
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
.carousel-img{
  cursor: pointer;
}
</style>
