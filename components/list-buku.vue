<template>
    <tbody>
        <tr>
            <td align="center">{{ id }}</td>
            <td align="center">{{ judul }}</td>
            <td align="center">{{ deskripsi }}</td>
            <td align="center">
                <nuxt-link :to="'/list-buku/' + id" style="text-decoration:  none;">
                    <v-btn small outlined color="info" >Detail</v-btn>
                </nuxt-link>
               <nuxt-link :to="'/list-buku/' + id + '/edit'" style="text-decoration:  none;">
                    <v-btn small outlined color="warning">Ubah</v-btn>
               </nuxt-link>
                    <v-btn small outlined @click="hapus" color="error">Hapus</v-btn>
            </td>
        </tr>
    </tbody>
</template>

<script>

export default {
    props:{
        id: {
            type: String,
            default: ''
        },
        judul: {
            type: String,
            default: ''
        },
        deskripsi:{
            type: String,
            default: ''
        },
    },

    methods:{
        hapus(){
            const hapus1 = confirm('Apakah anda yakin ingin mengahapus data?')
            if(!hapus1){
                return
            };

            const hapus2 = confirm('Apakah anda benar - benar yakin ingin menghapus data ini?')
            if(!hapus2){
                return
            };

            this.$axios.delete('http://localhost:3001/bukus/' + this.id)
            .then((del) => {
                this.$emit('refresh-ah');
            });
        },
    }
}
</script>