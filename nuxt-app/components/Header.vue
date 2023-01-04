<template>
  <header class="header">
    <div class="container">
      <div class="header-content col-12">
        <div class="header-logo-wrapper">logo</div>
        <div class="header-address col-lg-4">
          <span class="header-address">
            <i class="bi bi-geo-alt"></i> 660079, г. Красноярск, ул. 60 лет
            Октября, д. 121
          </span>
        </div>
        <div class="contacts">
          <h2>
            <a href="tel:+891393939391"
              ><i class="bi bi-telephone-forward"></i> 891393939391</a
            >
          </h2>
          <h5><i class="bi bi-envelope-at"></i> test@gmail.com</h5>
        </div>
      </div>
    </div>
    <div class="nav col-12" ref="header">
      <div class="container">
        <div class="burger-menu" @click="toggleMenu"><i v-if="!menuOpen" class="bi bi-list"></i> <i v-else class="bi bi-x"></i> Меню сайта</div>
        <transition name="slide-down">
          <ul class="nav-list" v-if="menuOpen">
            <li class="nav-list-item" v-for="link in links">
              <a class="nav-list-link" :href="'#' + link.src">{{
                link.title
              }}</a>
            </li>
          </ul>
        </transition>
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
  window.addEventListener("resize", closeMenu);
});
onUnmounted(() => {
  window.removeEventListener("resize", closeMenu);
});
const menuOpen = ref(true);
const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};
const closeMenu = () => {
  menuOpen.value = false;
};
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
.contacts h2 a {
  color: white;
  text-decoration: none;
}
.nav-list {
  padding: 0.5rem;
  width: 100%;
  display: flex;
}
.nav {
  background-color: #1a7fe4;
  user-select: none;
}
.header-content {
  display: flex;
  justify-content: space-between;
}
.burger-menu {
  display: none;
  padding: 0.5rem;
  cursor: pointer;
}
.nav.fixed {
  position: fixed;
  top: 0;
  width: 100%;
}
@media screen and (max-width: 576px) {
  .header-content {
    flex-direction: column;
    align-items: flex-start;
  }
  .nav-list {
    flex-direction: column;
  }
  .burger-menu {
    display: block;
  }
  .header-address{
    font-size: 14px;
  }
  .header-content *{
    margin: 0.5rem 0;
  }
}
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease-out;
}
.slide-down-enter-from,
.slide-down-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
