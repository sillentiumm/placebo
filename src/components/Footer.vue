<template>
  <footer>
    <div class="container">
      <div class="header">
        <h3>Новогодний корпоратив</h3>
        <div class="header__text">
          <p>
            Стильные залы с декором и крафтовой мебелью. Качественный звук, авторская кухня, нет «пробки»
          </p>
          <a href="#" class="shine">Подробнее →</a>
        </div>
      </div>
      <div class="footer">
        <div class="footer__left">
          <div class="address">
            <div
              v-for="card in addresses"
              :key="card.id"
              class="address__info"
            >
              <h4 class="address__title"> {{ card.title }} </h4>
              <div class="address__descr"> {{ card.descr }} </div>
              <div class="address__phone"> {{ card.phone }} </div>
              <div class="address__mail"> {{ card.mail }} </div>
            </div>
          </div>
          <div class="footer__left__descr">
            <p>Будни: 10:00—20:00</p>
            <p>Выходные: 11:00—19:00</p>
          </div>
        </div>
        <div class="footer__right">
          <div class="messengers">
            <div class="messengers__fulllinks">
              <a href="#" class="messengers__fulllink">Telegram</a>
              <a href="#" class="messengers__fulllink">WhatsApp</a>
            </div>
            <div class="messengers__icons">
              <a href="#" class="messengers__icon">
                <img src="@/assets/images/icons/vk.svg" alt="vk">
              </a>
              <a href="#" class="messengers__icon">
                <img src="@/assets/images/icons/zen.svg" alt="zen">
              </a>
              <a href="#" class="messengers__icon">
                <img src="@/assets/images/icons/instagram.svg" alt="instagram">
              </a>
              <a href="#" class="messengers__icon">
                <img src="@/assets/images/icons/facebook.svg" alt="facebook">
              </a>
            </div>
          </div>
          <div class="footer__right__descr">
            <p>Пишите круглосуточно.</p>
            <p>Ответим в рабочее время</p>
          </div>
        </div>
      </div>

      <div class="subfooter">
        <div class="subfooter__text">
          <div class="subfooter__text__column">
            <p>ООО «ЛОФТ ЭВЕНТ ХОЛЛ». Все права защищены. © 2015 — 2022 </p>
            <p>«LOFT HALL» является зарегистрированным товарным знаком. </p>
            <p>Свидетельство № 777531 выдано Федеральной службой по интеллектуальной собственности 30.09.2020.</p>
          </div>
          <div class="subfooter__text__column">
            <p>Юр. адрес: 115280, город Москва, ул. Ленинская Слобода, д. 26, пом. II-II, комн. 11  </p>
            <p>ИНН/КПП: 7725360042 /772501001   ОГРН: 1177746215690</p>
            <p>Перепечатка и любое использование материалов возможно только при наличии ссылки на первоисточник.</p>
          </div>
        </div>
        <div class="subfooter__details">
          <a href="#" class="subfooter__logo">
            <img src="@/assets/images/icons/logo.svg" alt="logo">
            <span>Part of Placebo/25</span>
          </a>
          <ButtonAnimate :title="'Мобильная версия'"/>
          <ButtonAnimate :title="'Скачать logo'"/>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>

import { reactive } from 'vue';
import ButtonAnimate from './UI/ButtonAnimate.vue'

const addresses = reactive([
  { id:1, title:'Москва', descr: 'Ленинская Слобода 26с15', phone: '+7 (495) 120-19-05', mail: 'info@lofthall.ru' },
  { id:1, title:'Подмосковье', descr: 'Ленинская Слобода 26с15', phone: '+7 (495) 120-19-05', mail: 'info@lofthall.ru' },
  { id:1, title:'Санкт-Петербург', descr: 'Арсенальная набережная 1', phone: '+7 (812) 317-12-20', mail: 'spb@lofthall.ru' }
])

</script>

<style scoped>
.container {
  max-width: 1210px;
  margin: 0 auto;
}
.header {
  position: relative;
  color: #fff;
  background-color: #151B63;
  border-radius: 20px;
  margin-bottom: 108px;
  padding-left: 42px;
  padding-right: 28px;
  padding-top: 32px;
  padding-bottom: 32px;
}
.header::after {
  position: absolute;
  content:'';
  width: 96%;
  height: 8px;
  bottom: -8px;
  left: 2%;
  background-color: #0C0F3A;
  border-radius: 0 0 20px 20px ;
}
h3 {
  font-weight: 500;
  font-size: 22px;
  color: #ffffff;
}
.header__text {
  display: flex;
  justify-content: space-between;
}
.header__text p {
  font-weight: 500;
  font-size: 14px;
  line-height: 19px;
  opacity: 0.72;
  color: #ffffff;
}
.header__text a {
  font-weight: 500;
  font-size: 14px;
  text-align: left;
  color: #ffffff;
  text-decoration: none;
}
.footer {
  display: flex;
  border-bottom: 1px solid #333333;
  padding-bottom: 64px;
  margin-bottom: 28px;
}
.footer__left {
  position: relative;
  display: flex;
  flex-direction: column;
  flex-basis: 60%;
}
.footer__left::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 1px;
  height: 100%;
  background-color: #333333;
}
.footer__left__descr {
  font-weight: 400;
  font-size: 12px;
  line-height: 19px;
  color: #808080;
  padding-bottom: 32px;
}
.footer__right {
  flex-basis: 40%;
}
.footer__right__descr {
  font-weight: 400;
  font-size: 12px;
  color: #808080;
  padding-left: 58px;
}
.address {
  width: 100%;
  display: flex;
  margin-bottom: 64px;
}
.address__info {
  width: 33%;
}

.address__title {
  font-weight: 600;
  font-size: 22px;
  color: #ffffff;
  margin-bottom: 4px;
}
.address__descr {
  font-weight: 400;
  font-size: 14px;
  color: #7f7f7f;
  margin-bottom: 18px;
}
.address__phone, .address__mail {
  font-weight: 400;
  font-size: 14px;
  color: #ffffff;
  margin-bottom: 4px;
}

.messengers {
  display: flex;
  padding-left: 4px;
  padding-right: 4px;
  margin-bottom: 20px;
}
.messengers__fulllinks {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
  flex-basis: 50%;
}
.messengers__fulllink {
  width: 90px;
  height: 28px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 300;
  font-size: 16px;
  color: #ffffff;
  text-decoration: none;
  border: 1px solid #464646;
  border-radius: 10px;
}
.messengers__icons {
  display: flex;
  justify-content: flex-end;
  gap: 8px; 
  flex-basis: 50%;
}
.messengers__icon {
  width: 30px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #1F1E1E;
  border-radius: 50%;
}
.subfooter {
  display: flex;
  justify-content: space-between;
  margin-top: 42px;
  margin-bottom: 64px;
  padding-left: 4px;
  padding-right: 4px;
}
.subfooter p {
  font-weight: 400;
  font-size: 12px;
  line-height: 16px;
  color: #565656;
  margin-bottom: 16px;
}
.subfooter__text {
  width: 50%;
  display: flex;
  justify-content: space-between;
  gap: 40px
}
.subfooter__details {
  display: flex;
  flex-direction: column;
  gap: 8px
}
.subfooter__logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  margin-bottom: 40px;
}
.subfooter__logo span {
  font-weight: 600;
  font-size: 12px;
  color: #565656;
  margin-left: 8px;
}
.subfooter__btn {
  width: 138px;
  height: 36px;
  color: #565656;
  background-color: transparent;
  border-radius: 8px;
  border: 1px  solid #505050;
  cursor: pointer;
}
</style>