<template>
  <div>
    <carousel :settings="settings">
    <slide class="card__wrapper" v-for="item in items" :key="item.id">
      <Card
        :name="`${item.lvl} lvl`"
        :title="item.title"
        :imgUrl="item.img"
        :link="`/${item.alias}`">
        <template v-slot:body>
          <p>
            {{ item.descr }}
          </p>
        </template>
        <template v-slot:footer>
          <div class="card-stats" >
            <CardStatItem
              class="one-third"
              :title="stat.title"
              :value="stat.value"
              v-for="(stat, index) in item.info"
              :key="index">
            </CardStatItem>
          </div>
        </template>
      </Card>
    </slide>

    <template #addons>
      <navigation />
    </template>
  </carousel>
  </div>
</template>

<script>
  import items from '@/seeders/items';
  import Card from '@/components/UI/Card.vue';
  import CardStatItem from '@/components/UI/CardStatItem.vue';

  import 'vue3-carousel/dist/carousel.css';
  import { Carousel, Slide, Navigation } from 'vue3-carousel';

  export default {
    components: {
      Card,
      CardStatItem,
      Carousel,
      Slide,
      Navigation,
    },
    data() {
      return {
        items,
        settings: {
          itemsToShow: 1,
          wrapAround: true,
          breakpoints: {
            480: {
              itemsToShow: 2,
            },
          },
        },
      }
    }
  }
</script>