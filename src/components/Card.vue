<script setup>
defineProps({
  item: Object
})
</script>
<template>
  <div class="card">
  <div class="card__image">
    <video autoplay muted loop="loop" :poster="item.image" playsinline="" v-if="item.video"><source :src="item.video" type="video/mp4" ></video>
    <img :src="item.image" alt="" v-else>
  </div>
    <div class="card__content">

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
</style>
