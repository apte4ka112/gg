<script setup>
import { computed} from 'vue'
const props = defineProps({
  item: Object
})
const emit = defineEmits(['load'])
const setLoyaut = () => {
  emit('load')
}

const className = computed(() => {
  if(props.item.category?.list) {
    let list = props.item.category?.list.map((item) => {
      return item.name
    })
    return props.item.category?.name + ' ' + list.join('')
  }
  else  {
    return props.item.category?.name
  }

})
</script>
<template>
  <div class="card" :class="className">
  <div class="card__image">
    <video autoplay muted loop="loop" :poster="item.image" playsinline="" v-if="item.video"><source :src="item.video" type="video/mp4" ></video>
    <img :src="item.image" @load="setLoyaut"  alt="" v-else>
  </div>
    <div class="card__content">

      <div class="card__tags" v-if="item.category?.title">
        <div class="tag active" v-if="item.category?.title">{{ item.category.title }}</div>
        <div class="tag" v-for="el in item.category?.list">{{el.title}}</div>
      </div>
      <div class="card__text">{{item.name}}</div>
    </div>
  </div>
</template>

<style lang="scss">
.card {
  position: relative;
  border-radius: 24px;
  overflow: hidden;
  cursor: pointer;
  width: 400px;
  margin-bottom: 20px;
  @media (max-width: 1400px) {
    width: calc(50% - 20px);
  }
  @media (max-width: 768px) {
    width: 100%;
  }
  &__tags {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 8px;

  }
  &:hover {
    .card__image {
      transform: scale(1.05);
    }
  }
  video {
    max-width: 100%;
    display: block;
  }
  &__image {
    transition: all .2s ease-out;


    img {
      max-width: 100%;
    }
  }
  &__content {
    position: absolute;
    bottom: 0;
    left: 6px;
    right: 6px;
    bottom: 6px;
    padding: 8px 14px;
    text-align: left;
    border-radius: 20px;
    backdrop-filter: blur(24px);
    background: rgba(0, 0, 0, 0.7);
    color: #fff;
  }
}
.tag{
  &.active {

    background: var(--color-brand);

color: #fff;
  }
  padding: 2px 4px 2px 4px;
  font-size: 14px;
  font-weight: 500;
  height: 24px;
  border-radius: 8px;
  display: inline-flex;
  background: #fff;
  color: var(--color-secondory-text);
}
</style>
