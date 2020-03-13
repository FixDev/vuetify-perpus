<template>
  <div>
    <!-- <Navigation></Navigation> -->
    <Carousel />
    <KatFilter />
    <Card />
  </div>
</template>

<script>
// import Navigation from '~/components/content/navbar.vue'
import Carousel from '~/components/content/carousel.vue'
import KatFilter from '~/components/content/filter-kat.vue'
import Card from '~/components/content/card.vue'

export default {
  components: {
    // Navigation,
    Carousel,
    KatFilter,
    Card
  }
};
</script>
