<template>
  <div>
    <div class="my-2">
      <v-btn small outlined color="primary" @click="search">Search</v-btn>
      <v-text-field
        v-model="query"
        label="Search"
        append-icon="mdi-magnify"
      ></v-text-field>
    </div>
    <v-btn class="mx-2" fab dark color="indigo">
      <v-icon dark>mdi-plus</v-icon>
    </v-btn>
    <!-- content -->
    <p v-if="isError">Error Tidak Mendapatkan Data</p>
    <p v-else-if="isEmpty">Data Tidak Ada Pada Table</p>
    <v-simple-table v-else-if="!isLoading" class="mx-auto">
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-center">ID</th>
            <th class="text-center">Judul</th>
            <th class="text-center">Kategori</th>
            <th class="text-center">Action</th>
          </tr>
        </thead>
        <ListItem
          v-for="buku in bukus"
          :id="buku.id"
          :key="buku.id"
          :judul="buku.judul"
          :kategori="buku.kategori"
          @refresh-ah="getData"
        >
        </ListItem>
      </template>
    </v-simple-table>
    <v-progress-circular
      v-else
      indeterminate
      color="primary"
    ></v-progress-circular>
    <!-- end-content -->
  </div>
</template>

<script>
import ListItem from "~/components/list-buku.vue";
export default {
  components: { ListItem },
  data() {
    return {
      bukus: [],
      isError: false,
      isEmpty: false,
      isLoading: false,
      query: ""
    };
  },
  mounted() {
    this.getData();
  },

  methods: {
    async search() {
      this.isLoading = true;

      try {
        const res = await this.$axios.get("http://localhost:3001/bukus", {
          params: {
            q: this.query
          }
        });
        this.bukus = res.data;

        if (this.bukus.length === 0) {
          this.isEmpty = true;
        }
      } catch (err) {
        this.isError = true;
      }
      this.isLoading = false;
    },
    async getData() {
      this.isLoading = true;

      try {
        const res = await this.$axios.get("http://localhost:3001/bukus");
        this.bukus = res.data;

        if (this.bukus.length === 0) {
          this.isEmpty = true;
        }
      } catch (err) {
        console.error(err);

        this.isError = true;
      }

      this.isLoading = false;
    }
  },
  computed: {
    filteredBukus: function() {
      return this.bukus.filter(buku => {
        return buku.title.match(this.search);
      });
    }
  }
};
</script>

<style lang="css" scoped>
.spin {
  width: 5rem;
  height: 5rem;
  margin: 0 auto;
  position: fixed;
  top: 50%;
  left: 47%;
}
</style>
