<template>
    <tbody>
        <tr>
            <td>{{ id }}</td>
            <td>{{ judul }}</td>
            <td>{{ kategori }}</td>
            <td>
                <nuxt-link :to="'/li-post/' + id">
                    <button class="btn btn-sm btn-primary">Detail</button>
                </nuxt-link>
               <nuxt-link :to="'/li-post/' + id + '/edit'">
                    <button class="btn btn-sm btn-warning">Ubah</button>
               </nuxt-link>
                    <button @click="hapus" class="btn btn-sm btn-danger">Hapus</button>
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
        kategori:{
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

            this.$axios.delete('http://localhost:3001/buku/' + this.id)
            .then((del) => {
                this.$emit('muat-ulang');
            });
        },
    }
}
</script>