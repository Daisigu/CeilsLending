<template>
  <header class="header">
    <div class="container">
      <div class="header-content col-12">
        <div class="header-logo-wrapper">logo</div>
        <div class="header-address col-lg-4 col-sm-12">
          <span> 660079, г. Красноярск, ул. 60 лет Октября, д. 121 </span>
        </div>
        <div class="contacts">
          <h2>891393939391</h2>
          <h5>test@gmail.com</h5>
        </div>
      </div>
    </div>
    <div class="nav col-12" ref="header">
      <div class="container">
        <ul class="nav-list">
          <li class="nav-list-item" v-for="link in links">
            <a class="nav-list-link" :href="'#' + link.src">{{ link.title }}</a>
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script setup>
const links = ref([
  {
    title: "Главная",
    src: "main",
  },
  {
    title: "Калькулятор",
    src: "calculator",
  },
  {
    title: "Стоимость",
    src: "price",
  },
  {
    title: "Наши работы",
    src: "works",
  },
]);
const header = ref(null);
onMounted(() => {
  window.addEventListener("scroll", () => {
    if (window.scrollY > header.value.offsetTop) {
      header.value.classList.add("fixed");
    } else {
      header.value.classList.remove("fixed");
    }
  });
});
</script>

<style scoped>
.header {
  background-color: rgb(46, 71, 199);
  color: #fff;
  padding-top: 0.5rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  z-index: 1;
  position: sticky;
}
.nav-list-link {
  color: #fff;
  text-decoration: none;
  margin-left: 1rem;
}
.nav-list {
  padding: 0.5rem;
  width: 100%;
  display: flex;
}
.nav {
  background-color: #1a7fe4;
}
.header-content {
  display: flex;
  justify-content: space-between;
}

.nav.fixed {
  position: fixed;
  top: 0;
  width: 100%;
}
</style>
