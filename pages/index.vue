<template>
  <div>
    <Carousel />
    <v-row
    align="center"
    justify="center">
      <v-btn-toggle v-model="toggle_exclusive">
        <KatFilter
        v-for="kat in kategoris"
        :key="kat.nama"
        :nama="kat.nama"
        ></KatFilter>
      </v-btn-toggle>
    </v-row>
    
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
  },

  data(){
    return{
      kategoris:[],
      toggle_exclusive: undefined,
    };
  },

  mounted(){
    this.getData();
  },

  methods:{
    async getData(){
      const res = await this.$axios.get('http://localhost:3001/kategoris');
      this.kategoris = res.data;
    }
  }
};
</script>
