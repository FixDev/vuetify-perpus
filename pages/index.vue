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
    
    <v-row
    align="center"
    justify="center">
    <!-- .slice(0,3) memfilter dari data ke 0 sampai data ke 2 yang di tampilkan dalam satu halaman -->
      <Card
      v-for="buku in bukus.slice(0,3)"
      :key="buku.id"
      :id="buku.id"
      :judul="buku.judul"
      :penulis="buku.penulis"
      :deskripsi="buku.deskripsi"></Card>
    </v-row>
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
      bukus:[],
      kategoris:[],
      toggle_exclusive: undefined,
    };
  },

  mounted(){
    this.getData();
  },

  methods:{
    async getData(){
      const res1 = await this.$axios.get('http://localhost:3001/kategoris');
      this.kategoris = res1.data;
      const res2 = await this.$axios.get('http://localhost:3001/bukus');
      this.bukus = res2.data;

    },
  }
};
</script>
