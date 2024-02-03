<script setup>
import { ref } from 'vue'
import menuIcon from '../assets/icon/menu.vue'
import siteIcon from '../assets/icon/site.vue'
import logoSmall from '../assets/icon/logo-small.vue'
import smiIcon from '../assets/icon/smi.vue'
import reklamaIcon from '../assets/icon/reklama.vue'
import newsIcon from '../assets/icon/news.vue'
const activeTabs = ref(0)

const navigation = ref([
  {
    name: 'Все',
    icon: menuIcon,
    link: '#'
  },
  {
    name: 'Сайты',
    icon: siteIcon,
    link: '#'
  },
  {
    name: 'Бренды',
    icon: logoSmall,
    link: '#'
  },
  {
    name: 'СММ',
    icon: smiIcon,
    link: '#'
  },
  {
    name: 'Реклама',
    icon: reklamaIcon,
    link: '#'
  },
  {
    name: 'Статьи',
    icon: newsIcon,
    link: '#'
  }
])
</script>
<template>
  <div class="navigation">
    <div class="navigation__item  " :class="{
      'active' : activeTabs == index
    }" v-for="(item,index) in navigation" :key="index" @click="activeTabs = index">
      <div class="navigation__item-icon">
        <component :is="item.icon" />
      </div>
      <div class="navigation__item-text">
        {{ item.name }}
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