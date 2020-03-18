<template>
    <div>
        <v-container fluid>
            <v-row
                style="padding: 4px 10px;"
                align="center"
                justify="justify">
                <v-card
                    class="mx-auto"
                    max-width="300px"
                >
                    <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                    height="200px">
                    <v-card-title style="color: white; text-shadow: 1.4px 0.8px grey;">{{ judul }}</v-card-title>
                    </v-img>

                    <v-card-subtitle>{{ penulis }}</v-card-subtitle>

                    <v-card-text class="text--primary">
                    <div>{{ deskripsi }}</div>
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
    props:{
        id:{
            type: String,
            default: ''
        },

        judul:{
            type: String,
            default:''
        },

        deskripsi:{
            type: String,
            default: ''
        },

        penulis:{
            type: String,
            default: ''
        }
    }
  }
</script>