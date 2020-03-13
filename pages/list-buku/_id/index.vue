<template>
  <v-card style="width: 100%" class="mx-auto" max-width="344">
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>

    <v-card-title> {{ buku.judul }} </v-card-title>
    <v-card-subtitle> Penulis :{{ buku.penulis }} </v-card-subtitle>

    <v-card-actions>
      <nuxt-link style="text-decoration: none;" to="/list-buku">
        <v-btn text>Kembali</v-btn>
      </nuxt-link>
      <v-btn color="purple" text>
        Edit
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? "mdi-eye-off" : "mdi-eye" }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          {{ buku.deskripsi }}
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      buku: {},
      id: this.$route.params.id
    };
  },
  mounted() {
    this.$axios
      .get("http://localhost:3001/bukus/" + this.$route.params.id)
      .then(res => {
        this.buku = res.data || {};
      });
  }
};
</script>
