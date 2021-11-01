<template>
  <div class="card">
    <div v-if="imgUrl" class="card__wrapper-img">
      <img class="card-img" :src="imgUrl" :alt="title">
    </div>
    <span class="card__name">{{ name }}</span>
    <span class="card__title">{{ title }}</span>
    <div class="card__body">
      <slot name="body"></slot>
      <router-link class="link link_card" v-if="link" :to="link">See more</router-link>
    </div>
    <slot name="footer"></slot>
  </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
        required: true,
      },
      title: {
        type: String,
        required: true,
      },
      imgUrl: {
        type: String
      },
      link: {
        type: String
      }
    }
  }
</script>