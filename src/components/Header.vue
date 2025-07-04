<template>
  <header class="header">
    <div class="background">
      <img src="@/assets/images/header-bg.png" alt="search">
    </div>
    <div class="header__container">
      <div class="header__menu">
        <a href="#" class="logo">
          LOFT
          HALL
        </a>
        <nav>
          <ul>
            <li
              v-for="city in navCities"
              :key="city.id"
              :class="city.active? 'navigation_enabled' : 'navigation_disabled'"
            >
              <a :href="city.href">
                {{ city.title }}
              </a>
            </li>
          </ul>
        </nav>
        <nav class="navigation">
          <ul>
            <li v-for="nav in navigation" :key="nav.id">
              <a :href="nav.href">
                {{ nav.title }}
              </a>
            </li>
          </ul>
        </nav>
      </div>
      <div class="header__main">
        <h2 :class="{ 'show': titleVisible }">
          авторские event- пространтсва в москве
        </h2>
        <p :class="{ 'show': descrVisible }">
          Первоклассный сервис, изысканная кухня, стильные интерьеры и полное техническое оснащение
        </p>
      </div>
      <div class="header__contacts">
        <p>+7 495 120-19-05</p>
        <button class="header__button shine">Перезвоните мне</button>
      </div>
    </div>
  </header>
</template>

<script setup>

import { ref, reactive, onMounted } from 'vue'

const navCities = reactive([
  { id: 1, title: 'Москва', href:'#', active: true },
  { id: 2, title: 'Санкт-Петербург', href:'#', active: false },
  { id: 3, title: 'Подмосковье', href:'#', active: false }
])
const navigation = reactive([
  { id: 1, title: 'Лофты', href:'#' },
  { id: 2, title: 'Залы', href:'#' },
  { id: 3, title: 'Мероприятия', href:'#' },
  { id: 4, title: 'Внутри', href:'#' },
  { id: 5, title: 'Кейтеринг', href:'#' },
  { id: 6, title: 'О нас', href:'#' },
  { id: 7, title: 'Журнал', href:'#' },
  { id: 8, title: 'Контакты', href:'#' }
])

const titleVisible = ref(false)
const descrVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    titleVisible.value = true;
  }, 500);
    setTimeout(() => {
    descrVisible.value = true;
  }, 1000);
});

</script>

<style scoped>
  nav {
    color: #fff;
    font-weight: 500;
    font-size: 12px;
    font-family: 'Manrope';
    line-height: 18px;
  }
  a {
    color: #fff;
    text-decoration: none;
  }
  .background {
    width: 100%;
    max-height: 720px;
    position: absolute;
    left: 0;
    top: 0;
    background-color: #000;
    z-index: -1;
  }
  .background::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 160px;
    background: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 1));
  }
  .background img {
    width: 100%;
    max-height: 720px;
    opacity: .36;
    opacity: .25;
  }
  .header {
    position: relative;
    height: 720px;
    padding: 24px;
    z-index: 10;
  }
  .header__container {
    max-width: 1920px;
    height: 100%;
    max-height: 720px;
    display: grid;
    grid-template-columns: 2fr 1fr 2fr;
    margin: 0 auto;
  }
  .header__menu {
    margin-top: 4px;
  }
  .logo {
    width: 62px;
    height: 62px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #fefefe;
    font-size: 22px;
    text-align: center;
    color: #000;
    border-radius: 50%;
    border: 1px solid #fefefe;
    overflow: hidden;
    margin-bottom: 34px;
  }
  .navigation {
    margin-top: 16px;
  }
  .navigation li {
    list-style: none;
  }
  .navigation li:hover {
    text-decoration: underline;
  }
  .navigation_enabled {
    list-style: outside;
  }
  .navigation_disabled {
    list-style: none;
  }
  .navigation_disabled a {
    color: #5B5B5B;
    cursor: auto;
  }
  .header__main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    color: #fff;
    align-self: center;
  }
  .header__main h2 {
    font-family: 'Lithium_tf', sans-serif;
    font-weight: 400;
    font-size: 60px;
    line-height: 56px;
    letter-spacing: 3px;
    text-align: center;
    text-transform: uppercase;
    transition: 6s;
    margin-bottom: 16px;
    opacity: 0;
  }
  .header__main p {
    font-family: 'Manrope';
    font-weight: 400;
    font-size: 14px;
    line-height: 21px;
    letter-spacing: 0.2px;
    text-align: center;
    color: #c7c7c7;
    transition: 6s;
    padding-left: 36px;
    padding-right: 36px;
    opacity: 0;
  }
  .header__contacts {
    height: 36px;
    display: flex;
    justify-content: end;
    align-items: center;
  }
  .header__contacts p {
    color: #fff;
    font-family: 'Manrope';
    font-weight: 600;
    font-size: 14px;
    letter-spacing: 2px;
    margin-right: 28px;
  }
  .header__button {
    width: 156px;
    height: 36px;
    background-color: #fff;
    font-family: 'Manrope';
    font-weight: 600;
    font-size: 14px;
    text-align: center;
    border-radius: 10px;
    border: none;
    cursor: pointer;
  }
  .show {
    opacity: 1 !important;
  }
</style>