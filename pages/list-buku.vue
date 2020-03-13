<template>
  <v-card>
    <v-card-title>
      <v-text-field
        v-model="search"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :search="search"
    >
    <ListBuku v-for="buku in bukus"
    :key="buku.id"
    :id="buku.id"
    :judul="buku.judul"
    :kategori="buku.kategori"
    > </ListBuku>
    </v-data-table>
  </v-card>
</template>

<script>
import ListBuku from '~/components/list-buku.vue'
  export default {
    components: {
        ListBuku
    },
    data () {
      return {
        bukus: [],
        search: '',
        headers: [
          { text: 'Id', value: 'id' },
          {
            text: 'Nama Buku',
            align: 'start',
            value: 'name',
          },
          { text: 'Kategori', value: 'cat' },
          { text: 'Action', value: 'act' }
        ],
      }
    },
    mounted(){
        this.getData()
    },
    methods: {
        async getData(){
            try{
                const res = await this.$axios.get('http://localhost:3001/buku')
                this.bukus = res.data;
            } catch(err) {
            console.error(err);   
        }
        }
    }
  }
</script>

<style>

</style>