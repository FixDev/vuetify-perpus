<template>
  <div>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="buku.id"
          label="Id"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="buku.judul"
          label="Judul"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="buku.deskripsi"
          label="Deskripsi"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="4"> </v-col>
      <v-col cols="12" sm="4">
        <v-text-field
          v-model="buku.penulis"
          label="Penulis"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="7" sm="4"> </v-col>
      <v-col cols="5" sm="4">
        <v-btn @click.prevent="simpan" color="success" large dark>
          Simpan
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>

export default {

  data() {
    return {
      buku: {},
    };
  },
  methods: {
    simpan() {
      this.$axios.post("http://localhost:3001/bukus", this.buku).then(send => {
        this.$router.push("/list-buku");
      });
    }
  }
};
</script>
