<template>
  <div>
    <Carousel />
    <KatFilter />
    <Card />
  </div>
</template>

<script>
import Carousel from '~/components/content/carousel.vue'
import KatFilter from '~/components/content/filter-kat.vue'
import Card from '~/components/content/card.vue'

export default {
  components: {
    Carousel,
    KatFilter,
    Card
  }
};
</script>
