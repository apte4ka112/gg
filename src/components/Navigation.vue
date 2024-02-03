<script setup>
import {onMounted, ref} from 'vue'
import menuIcon from '../assets/icon/menu.vue'
import siteIcon from '../assets/icon/site.vue'
import logoSmall from '../assets/icon/logo-small.vue'
import smiIcon from '../assets/icon/smi.vue'
import reklamaIcon from '../assets/icon/reklama.vue'
import newsIcon from '../assets/icon/news.vue'
const activeTabs = ref(0)
const emit = defineEmits(['setFilter'])
const navigation = ref([
  {
    name:'*',
    title: 'Все',
    id: 0,
    icon: menuIcon,
    category: [
      { title: 'Лендинги', name:'.lend', id: 2},

    ],
    link: '#'
  },
  {
    name:'.site',
    title: 'Сайты',
    icon: siteIcon,
    category: [
      { title: 'Корпаративные сайты' , name:'.corparat', id: 2},
      { title: 'Лендинги' , id: 3,  name:'.lend'}
    ],
    link: '#'
  },
  {
    name:'.brand',
    title: 'Бренды',
    icon: logoSmall,
    link: '#'
  },
  {
    title: 'СММ',
    icon: smiIcon,
    link: '#'
  },
  {
    title: 'Реклама',
    icon: reklamaIcon,
    link: '#'
  },
  {
    title: 'Статьи',
    icon: newsIcon,
    link: '#'
  }
])
onMounted(()=> {
  emit('setFilter', navigation.value[0])
})
</script>
<template>
  <div class="navigation">
    <div class="navigation__item  "   :class="{
      'active' : activeTabs == index
    }" v-for="(item,index) in navigation" :key="index" @click="activeTabs = index, emit('setFilter', item)">
      <div class="navigation__item-icon">
        <component :is="item.icon" />
      </div>
      <div class="navigation__item-text">
        {{ item.title }}
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.navigation {
  margin-top: 32px;
  display: flex;
  justify-content: center;
  gap: 34px;
  @media (max-width: 768px) {
    margin-left: -20px;
    margin-right: -20px;
    overflow: auto;
    justify-content: flex-start;
    padding-left: 50px;
    padding-right: 50px;
  }

  &__item {
    user-select: none;
    color: var(--color-secondory-text);
    cursor: pointer;
    transition: all .2s ease-out;

    path {
      fill:  var(--color-secondory-text);
    }
    &.active {
      color: var(--color-brand);
      cursor: default;
      .navigation__item-icon {
        background: var(--color-brand);
      }
      path {
        fill: #fff ;
      }
    }

    &:not(.active):hover {
     color: var(--color-secondory-text-hover);
      .navigation__item-icon {
        background: var(--color-secondory-bg-hover);
      }
      path {
        fill: var(--color-secondory-text-hover);
      }
    }
    &-icon {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 16px;
      gap: 10px;
      border-radius: 24px;
      background: var(--color-secondory);

      width: 64px;
      height: 64px;
    }
    &-text {
      margin-top: 4px;
      font-size: 14px;
      font-style: normal;
      font-weight: 500;
      line-height: 20px;
    }
  }
}
</style>