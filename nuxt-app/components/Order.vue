<template>
  <section class="order" id="price">
    <div class="container">
      <UITitleSubTitle
        title="Бесплатный вызов замерщика"
        sub-title="Квалифицированный технолог не допускает ошибок! Точная оценка стоимости работ"
      />
      <div class="order-content">
        <OrderForm
          btn-text="Вызвать замерщика"
          class="col-sm-12 col-lg-8"
          @on-submit="handleSubmit"
        />
        <div class="rabotyaga-wrapper">
          <img class="rabotyaga" src="@/assets/images/rabotyaga.jpg" alt="" />
        </div>
      </div>
    </div>
    <UI-Modal :open="confirmOrderModal" @close="confirmOrderModal = false">
      <template #header>
        <h1>Заявка принята</h1>
      </template>
      <template #main>
        Ваше сообщение успешно отправлено! Мы свяжемся с вами сразу после
        прочтения письма, обычно это не занимает много времени.
      </template>
    </UI-Modal>
  </section>
</template>

<script setup>
const confirmOrderModal = ref(false);
const handleSubmit = (formSubmitData) => {
  console.log(formSubmitData.value);
  confirmOrderModal.value = true;
  formSubmitData.value = {}
};
</script>

<style scoped>
.order {
  padding: 4rem 0;
}

.rabotyaga {
  width: 100%;
}
.order-content {
  display: flex;
}
@media screen and (max-width: 576px) {
  .rabotyaga-wrapper {
    display: none;
  }
}
</style>
