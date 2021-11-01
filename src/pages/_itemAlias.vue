<template>
  <div v-if="item" class="wrapper wrapper_person">
    <div>
      <img :src="item.img" :alt="item.title">
      <h1 class="title">{{ item.title }}</h1>
      <p>{{ item.descr }}</p>

      <div class="card-stats">
        <CardStatItem
          class="one-third"
          :title="stat.title"
          :value="stat.value"
          v-for="(stat, index) in item.info"
          :key="index">
        </CardStatItem>
      </div>

      <router-link to="/" class="btn btn-primary">back to home</router-link>
    </div>
  </div>
</template>

<script>
  import items from '@/seeders/items';
  import CardStatItem from '@/components/UI/CardStatItem.vue';

  export default {
    data() {
      return {
        item: null,
      }
    },
    components: {
      CardStatItem
    },
    created() {
      const alias = this.$route.params.itemAlias;
      const item = items.find(el => el.alias === alias);
      if (!item) {
        this.$router.push({name: '404', hash: `/${alias}`});
      }
      this.item = item;
    }
  }
</script>

<style lang="scss" scoped>
  .wrapper_person {
    text-align: center;

    .card-stats {
      margin: 30px 0;
      border-radius: 14px;
    }
  }
</style>