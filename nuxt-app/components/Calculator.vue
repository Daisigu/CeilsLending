<template>
  <section id="calculator" class="calculator">
    <div class="container">
      <UI-TitleSubTitle
        :title="'Калькулятор стоимости потолка'"
        :sub-title="'Расчет онлайн прямо у нас на сайте'"
      />
      <div class="calculator-content">
        <div
          v-for="input in inputs"
          class="input-wrapper col-12 col-lg-4 col-md-6"
        >
          <label for="">{{ input.title }}</label>
          <input
            v-model.trim.number="input.value"
            class="calc-input"
            type="number"
            @change="startCounting(totalCost, 1000)"
          />
        </div>
        <div class="total-sum col-12 col-lg-4 col-md-6">
          <h1 class="totalCost">{{ currentValue }} ₽</h1>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const inputs = ref([
  {
    title: "Площадь потолка в метрах",
    value: 0,
  },
  {
    title: "Жопа  в метрах",
    value: 0,
  },
  {
    title: "Жопа  в метрах",
    value: 0,
  },
  {
    title: "Жопа  в метрах",
    value: 0,
  },
  {
    title: "Жопа  в метрах",
    value: 0,
  },
]);
const currentValue = ref(0);
const startCounting = (target, duration) => {
  const start = performance.now();
  const intervalId = requestAnimationFrame(function animate(time) {
    let timeFraction = (time - start) / duration;
    if (timeFraction > 1) timeFraction = 1;
    currentValue.value = (timeFraction * target).toFixed(0);
    if (timeFraction < 1) {
      requestAnimationFrame(animate);
    }
  });
  watch(currentValue, (newValue, oldValue) => {
    if (newValue >= target) {
      cancelAnimationFrame(intervalId);
    }
  });
};
const totalCost = computed(() => {
  return inputs.value.reduce((acc, item) => acc + item.value, 0);
});
</script>

<style scoped>
.calculator {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 4rem;
  padding-bottom: 4rem;
}
.totalCost{
  font-size: 40px;
}
.calculator-content {
  margin-top: 2rem;
  display: flex;
  flex-wrap: wrap;
}
.input-wrapper {
  display: flex;
  padding: 1rem;
  flex-direction: column;
}
.total-sum {
  display: flex;
  align-items: center;
  justify-content: center;
}
.calc-input {
  padding: 0.5rem;
}
@media screen and (max-width: 576px) {
.input-wrapper{
  padding: 0.5rem;
}
}
</style>
