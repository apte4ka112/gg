<script setup>
import {onMounted, ref} from 'vue'

import Navigation from '../components/Navigation.vue'
import Category from '../components/Category.vue'
import Card from '../components/Card.vue'
import Isotope from 'isotope-layout'

const category = ref([
  {
    name: 'Все',
    id: 1
  },
  {
    name: 'Анимированные',
    id: 2
  },
  {
    name: 'Клипы',
    id: 3
  },
  {
    name: 'Рилсы',
    id: 4
  }
])

const cards = ref([
  {
    image: 'https://img.brandshop.ru/cache/products/c/ctm-tdbb-0_1104x1104.jpg',
    name: 'Анимированные картинки нового поколения'
  },

  {
    image: 'https://img.artlebedev.ru/everything/akkuyu/morda/akkuyu-cover-1200.png',
    video: 'https://img.artlebedev.ru/everything/akkuyu/morda/akkuyu-cover-1200.mp4',
    name: 'Анимированные картинки нового поколения'
  },

  {
    image: 'https://img.artlebedev.ru/everything_files/images/9289/metro-promo-photo-1200.jpg.webp',
    name: 'Анимированные картинки нового поколения'
  },
  {
    image: 'https://img.artlebedev.ru/everything/atach/identity/morda/atach-1200.jpg',
    video: 'https://img.artlebedev.ru/everything/atach/identity/morda/atach-1200.mp4',
    name: 'Анимированные '
  },
  {
    image: 'https://img.brandshop.ru/cache/products/m/men_home_20240123_677x724.jpg',
    name: 'Анимированные картинки нового поколения'
  },
  {
    image: 'https://img.brandshop.ru/cache/products/c/ctm-tdbb-0_1104x1104.jpg',
    name: 'Анимированные картинки нового поколения'
  }
])
const activeTabs = ref(1)

const grid = ref(null);
let iso = null;
onMounted(() => {
  iso = new Isotope( grid.value, {
    // options...
    itemSelector: '.card',
    masonry: {
      columnWidth: 400,
      gutter: 20
    }
  });
})
</script>

<template>
  <div class="page">

  <Navigation class="animate__animated animate__fadeIn"/>
    <div class="page__category animate__animated animate__fadeIn">
      <Category @click="activeTabs = item.id" :active="item.id === activeTabs" v-for="item in category" :item="item" :key="item.id"/>
    </div>
    <div class="page__body"  >
      <div class="grid" ref="grid">
        <Card  :item="item" v-for="item in cards"/>
      </div>
    </div>
  </div>

</template>

<style lang="scss">
.page {
  &__category {
    margin-top: 28px;
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }
  &__body {
    margin-top: 36px;
    gap: 20px;
    margin-bottom: 54px;
  }
}
</style>