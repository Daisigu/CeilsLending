<template>
  <section id="main" class="main">
    <div class="container">
      <div class="main-block col-lg-6 col-md-8 col-12">
        <h1 class="main-title">Натяжные потолки, окна, балконы, ремонт</h1>
        <h5 class="main-subtitle">Дарим подарки на Новый год!</h5>
        <h5 class="main-subtitle">Звоните нам, расскажем условия акции</h5>
        <div class="main-cards">
          <div class="card">
            <div class="card-img">
              <img
                width="50"
                src="https://png.pngtree.com/png-vector/20190215/ourlarge/pngtree-vector-wallet-icon-png-image_515300.jpg"
              />
            </div>
            <div class="card-content">
              Беспроцентная рассрочка без банка и переплат
            </div>
          </div>
          <div class="card">
            <div class="card-img">
              <img
                src="https://img2.freepng.ru/20180619/zsl/kisspng-computer-icons-award-symbol-badge-5b288b60dc2c77.5500060915293837769018.jpg"
                width="50"
              />
            </div>
            <div class="card-content">
              5 лет гарантии на работы, 20 лет на изделия
            </div>
          </div>
          <div class="card">
            <div class="card-img">
              <img
                src="https://www.freepngimg.com/thumb/gears/177104-vector-gears-hd-image-free.png"
                width="50"
              />
            </div>
            <div class="card-content">Собственное производство с 2004 года</div>
          </div>
        </div>
        <UIButton @click="orderModal = true"> Рассчитать стоимость </UIButton>
      </div>
    </div>
    <UI-Modal :open="orderModal" @close="orderModal = false">
      <template #header>
        <h1>Рассчитать стоимость</h1>
      </template>
      <template #main>
        <OrderForm btnText="Рассчитать стоимость" @onSubmit="onSubmit" />
      </template>
    </UI-Modal>
    <UI-Modal :open="confirmOrderModal" @close="confirmOrderModal = false">
      <template #main>
        Ваше сообщение успешно отправлено! Мы свяжемся с вами сразу после
        прочтения письма, обычно это не занимает много времени.
      </template>
    </UI-Modal>
  </section>
</template>

<script setup>
const orderModal = ref(false);
const confirmOrderModal = ref(false);
const onSubmit = () => {
  confirmOrderModal.value = true;
  orderModal.value = false;
};
</script>
<style scoped>
.main {
  background-image: url("@/assets/images/main-bg.jpeg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  padding-top: 2rem;
  padding-bottom: 2rem;
}
.main-block {
  background-color: rgba(240, 248, 255, 0.904);
  padding: 1.5rem;
  border-radius: 0.3rem;
  margin: 6rem 0;
}
.main-block * {
  margin: 0.5rem 0;
}
.main-title {
  color: #1166bc;
  font-size: 30px;
}
.main-subtitle {
  font-size: 20px;
  font-weight: 500;
}
.main-cards {
  display: flex;
}
.main-cards .card {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.main-cards .card .card-img {
  margin-right: 1rem;
}
.card-img {
  mix-blend-mode: darken;
  z-index: 0;
}
.card-img img {
}
</style>
