<template>
    <div>
        <v-container fluid>
            <v-row
            :align="alignment"
            :justify="justify">
                <v-card
                    v-for="kat in categories"
                    :key="kat.judul"
                    class="mx-auto"
                    max-width="400"
                >
                    <v-img
                    class="white--text align-end"
                    height="200px"
                    :src="kat.img"
                    >
                    <v-card-title style="text-shadow: 1.4px 0.8px grey;">{{kat.judul}}</v-card-title>
                    </v-img>

                    <v-card-subtitle class="pb-0">{{ kat.penulis }}</v-card-subtitle>

                    <v-card-text class="text--primary">
                    <div>{{kat.desc}}</div>
                    </v-card-text>

                    <v-card-actions>
                    <v-btn
                        color="info"
                    >
                        Details
                    </v-btn>
                    <nuxt-link style="text-decoration: none;" :to="'/list-buku'">
                        <v-btn
                            color="orange"
                            text
                        >
                            Lainnya..
                        </v-btn>
                    </nuxt-link>
                    </v-card-actions>
                </v-card>
            </v-row>
        </v-container>
    </div>
</template>

<script>
  export default {
    data(){
        return{
            categories:[
                { judul: 'Sang Pangeran', penulis: 'Salim A Fillah', img: 'https://s1.bukalapak.com/img/10307414761/w-300/data.jpeg.webp', desc: 'Buku sejarah'},
                { judul: 'Isa Bin Maryam', penulis: 'Ali Muhammad Ash Shallabi', img: 'https://s1.bukalapak.com/img/19684331581/w-300/data.jpeg.webp', desc: 'Sejarah Nabi Isa'},
                { judul: 'Menjerat Gus Dur', penulis: 'Virdika Rizky Utama', img: 'https://s1.bukalapak.com/img/10945046191/w-300/data.jpeg.webp', desc: 'kosong'},
            ],
        }
    }
  }
</script>