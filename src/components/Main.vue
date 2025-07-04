<template>
  <section>
    <div class="container">
      <h3>Залы в Москве</h3>
      <ul>
        <li v-for="personCount, idx in listPersonCount" :key="personCount.id">
          <button
            @click="setActivePersonCount(idx)"
            :class="personCount.active? 'btn-active' : '' "
          >
            {{ personCount.title }}
          </button>
        </li>
      </ul>
      <ul>
        <li v-for="detail, idx in listDetails" :key="detail.id">
          <button 
            @click="setActiveDetails(idx)"
            :class="detail.active? 'btn-active' : ''"
          >
            {{ detail.title }}
          </button>
        </li>
      </ul>
      <div class="main__content">
        <div v-for="card in ListCards" :key="card.id" class="card">
          <img :src="getImageUrl(card.img)" alt="Image"/>
          <div class="card__text">
            <h4>{{ card.title }}</h4>
            <div class="card__minicards">
              <div
                v-for="minicard, index in card.cards"
                :ket="index"
                class="minicard"
              >
                {{ minicard }}
              </div>
              <p v-if=card.descr>{{ card.descr }}</p>
              <p v-if=card.secondDescr>{{ card.secondDescr }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'

const listPersonCount = reactive([
  { id:1, title: 'До 100', active: false },
  { id:2, title: 'До 500', active: false },
  { id:3, title: 'Больше 100', active: false },
  { id:4, title: 'Больше 500', active: false }
])
const listDetails = reactive([
  { id:1, title: 'Для стильной свадьбы', active: false },
  { id:2, title: 'Масштабная конференция', active: false },
  { id:3, title: 'Масштабная конференция', active: false },
  { id:4, title: 'Масштабная конференция', active: false }
])

const ListCards = reactive([
  { id: 1, title: 'Rockefellers Hall', img:'1.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'], descr: '', secondDescr: '' },
  { id: 2, title: 'Grace Hall', img:'2.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'], descr: '', secondDescr: '' },
  { id: 3, title: 'Montblank Hall', img:'3.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'],
    descr: 'Первоклассный сервис, изысканная кухня, стильные интерьеры и полное техническое оснащение, изысканная кухня, стильные интерьеры и полное техническое оснащение',
    secondDescr: 'Первоклассный сервис, изысканная кухня, стильные интерьеры и полное техническое оснащение' },
  { id: 4, title: 'Rockefellers Hall', img:'4.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'], descr: '', secondDescr: '' },
  { id: 5, title: 'Grace Hall', img:'5.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'], descr: '', secondDescr: '' },
  { id: 6, title: 'Montblank Hall', img:'6.jpg', cards: ['800м2', '200-400 персон', 'м.Повелецкая'], descr: '', secondDescr: '' },
])

const setActivePersonCount = (idx) => {
  if (listPersonCount[idx].active) {
    listPersonCount[idx].active = false
    return
  }
  listPersonCount.forEach(el => { el.active = false })
  listPersonCount[idx].active = true
}
const setActiveDetails = (idx) => {
  if (listDetails[idx].active) {
    listDetails[idx].active = false
    return
  }
  listDetails.forEach(el => { el.active = false })
  listDetails[idx].active = true
}

const getImageUrl = (path) => {
  return new URL(`../assets/images/main/${path}`, import.meta.url).href;
};

</script>

<style scoped>
.container {
  max-width: 1230px;
  margin: 0 auto;
  color: #fff;
}
h3 {
  margin-bottom: 16px;
}
ul {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
  margin-bottom: 8px;
}
li {
  list-style: none;
}
li button {
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  color: #d9d9d9;
  background-color: transparent;
  border: 1px solid #333333;
  border-radius: 18px;
  box-shadow: 0px 4px 4px rgba(0,0,0,0.25);
  padding: 8px 22px;
}
li button:hover {
  background-color: rgba(255,255,255,.1);
}
.btn-active {
  background-color: #d9d9d9;
  color: #000;
}
.btn-active:hover {
  background-color: #d9d9d9;
  opacity: .9;
}
.main__content {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding-top: 42px;
  padding-bottom: 144px;
}
.card {
  display: flex;
  flex-direction: column;
}
.card img {
  transition: .3s;
}
.card:hover img {
  transform: scale(1.05);
}
.card img {
  max-width: 390px;
  max-height: 390px;
  border-radius: 20px;
  overflow: hidden;
  margin-bottom: 28px;
}
.card__text {
  width: 390px;
  padding-left: 16px;
  padding-right: 16px;
  margin-bottom: 56px;
}
.card h4 {
  font-weight: 500;
  font-size: 22px;
  color: #ffffff;
  margin-bottom: 8px;
}
.card__minicards {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
}
.minicard {
  font-weight: 500;
  font-size: 14px;
  text-align: center;
  color: #d9d9d9;
  background: rgba(255,255,255,0.16);
  border-radius: 6px;
  padding: 2px 8px 4px;
}
.card p {
  font-size: 14px;
  line-height: 19px;
  color: #c7c7c7;
  padding-top: 16px;
}
</style>