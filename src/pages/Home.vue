<script setup>
import {onMounted, ref,nextTick} from 'vue'

import Card from '../components/Card.vue'
import Isotope from 'isotope-layout'
import Filter from '../components/Filter.vue'

const cards = ref([
  {
    image: 'https://img.brandshop.ru/cache/products/c/ctm-tdbb-0_1104x1104.jpg',
    name: 'Анимированные картинки нового поколения',
    category: {
      name: 'brand',
      title: 'Бренды',
    }
  },

  {
    image: 'https://img.artlebedev.ru/everything/akkuyu/morda/akkuyu-cover-1200.png',
    video: 'https://img.artlebedev.ru/everything/akkuyu/morda/akkuyu-cover-1200.mp4',
    category: {
      name: 'site',
      title: 'Сайты',
      list: [
        {
          name: 'lend',
          title: 'lend',
        }
      ]
    },
    name: 'Анимированные картинки нового поколения'
  },

  {
    image: 'https://img.artlebedev.ru/everything_files/images/9289/metro-promo-photo-1200.jpg.webp',
    name: 'Анимированные картинки нового поколения',
    category: 'desing'

  },
  {
    image: 'https://img.artlebedev.ru/everything/atach/identity/morda/atach-1200.jpg',
    video: 'https://img.artlebedev.ru/everything/atach/identity/morda/atach-1200.mp4',
    category: {
      name: 'site',
      title: 'Сайты',
      list: [
        {
          name: 'corparat',
          title: 'corparat',
        }
      ]
    },
    name: 'Анимированные '
  },
  {
    image: 'https://img.brandshop.ru/cache/products/m/men_home_20240123_677x724.jpg',
    name: 'Анимированные картинки нового поколения',
    category: 'desing'

  },
  {
    image: 'https://img.brandshop.ru/cache/products/c/ctm-tdbb-0_1104x1104.jpg',
    name: 'Анимированные картинки нового поколения'
  }
])

const grid = ref(null);
let iso = null;
const loading = ref(true);
const setLoyaut = () => {
  iso = new Isotope( grid.value, {
    // options...
    itemSelector: '.card',
    masonry: {
      gutter: 20,
    }
  });
}
const filterItems = (item ,load) => {
  if(iso) {

  iso.arrange({
    filter: item.name,
    sortBy: 'number'
  })
  }

// re-apply filtering, sorting, and layout
}
onMounted(() => {
  setTimeout(() => {
    loading.value = false
  }, "1000");
})
</script>

<template>
  <div class="page">
  <div class="animate__animated animate__fadeInUp">
    <Filter @setFilter="filterItems"/>

  </div>
    <div class="page__body"  >
      <div class="grid" ref="grid">
        <Card  @load="setLoyaut" :item="item" v-for="item in cards"  :class=" [{
          'animate__animated animate__slideInUp' : loading,
        }]"/>
      </div>
    </div>
  </div>

</template>

<style lang="scss">
.page {
  &__body {
    margin-top: 36px;
    gap: 20px;
    margin-bottom: 54px;
  }
}
</style>