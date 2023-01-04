<template>
  <section class="causes">
    <div class="container">
      <UI-TitleSubTitle
        :title="'Почему вы должны оставить заявку у нас'"
        :sub-title="'Высокое качество оказываемых услуг в сочетании с низкой стоимостью'"
      />
      <div class="causes-cards">
        <div class="card col-lg-3 col-md-6 col-12" v-for="card in cards">
          <div class="card-img-wrapper">
            <img
              class="card-img"
              :src="card.src"
              width="50"
              height="50"
              alt=""
            />
          </div>
          <h3 class="card-title">
            {{ card.title }}
          </h3>
          <p class="card-content">
            {{ card.content }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const cards = ref([
  {
    title: "Низкая цена",
    src: "https://w7.pngwing.com/pngs/428/841/png-transparent-currency-symbol-russian-ruble-dollar-sign-russia.png",
    content:
      "Собственное производство позволяет нам не только полностью контролировать весь производственный процесс, но и держать цену ниже рынка.",
  },
  {
    title: "Работаем без пыли и грязи",
    src: "https://www.seekpng.com/png/detail/524-5247314_-.png",
    content:
      "Используем перфораторы с пылесосом и сводим количество пыли к минимуму! Монтаж возможен даже в помещении после ремонта.",
  },
  {
    title: "Защитим ваши стены и мебель",
    src: "https://cdn-icons-png.flaticon.com/512/3210/3210102.png",
    content:
      "Если нам предстоит работать в помещении с мебелью и поклеенными обоями, то мы укроем ваше имущество прочной защитной пленкой.",
  },
  {
    title: "Используем гипоаллергенные материалы",
    src: "https://img.icons8.com/ios/500/paint-sprayer.png",
    content:
      "В своей работе мы применяем сертифицированные материалы, которые полностью безопасны (ГОСТ 24944-81).",
  },
]);
</script>

<style scoped>
.causes {
  background-color: #f3f6f9;
  padding-top: 4rem;
  padding-bottom: 4rem;
}
.causes-cards {
  display: flex;
  margin-top: 2rem;
  flex-wrap: wrap;
  text-align: center;
  justify-content: space-between;
}
.card-content {
  font-size: 13px;
}
.card-img-wrapper {
  mix-blend-mode: color-burn;
}
.card-title {
  margin-bottom: 1rem;
  font-size: 17px;
}
.card {
  padding: 1rem;
  padding-inline: 2rem;
  border: 1px solid lightgray;
  border-radius: 0.3rem;
  margin-right: 0rem;
}
</style>
