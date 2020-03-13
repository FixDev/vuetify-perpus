<template>
  <div>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="title"
          :rules="rules"
          label="Id"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4" class="d-flex">
        <ListKat
          v-for="kat in kategoris"
          :key="kat.id"
          :id="kat.id"
          :nama="kat.nama"
        >
        </ListKat>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="title"
          :rules="rules"
          label="Judul"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="title"
          :rules="rules"
          label="Deskripsi"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="title"
          :rules="rules"
          label="Penulis"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="7" sm="4"> </v-col>
      <v-col cols="5" sm="4">
        <v-btn color="success" large dark>
          Simpah
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ListKat from "~/components/content/list-kategori.vue";

export default {
  components: {
    ListKat
  },

  data() {
    return {
      bukus: {},
      kategoris: []
    };
  },
  methods: {
    async getData() {
      try {
        const res = await this.$axios.get("http://localhost:3001/kategoris");
        this.kategoris = res.data;
      } catch (err) {
        console.error(err);
      }
    },
    async simpan() {
      this.$axios.post("http://localhost:3001/bukus", this.buku).then(send => {
        this.$router.push("/list-buku");
      });
    }
  }
};
</script>
