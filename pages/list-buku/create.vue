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
        <v-select
          v-for="buku in bukus"
          :key="buku.kategori"
          :items="buku.kategori"
          label="Outlined style"
          dense
          outlined
        >Pilih Kategori</v-select>
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
      <v-col cols="7" sm="4">
      </v-col>
      <v-col cols="5" sm="4">
        <v-btn color="success" large dark>
          Simpah
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      buku: {}
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
