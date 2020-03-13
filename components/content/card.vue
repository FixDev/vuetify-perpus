<template>
    <div>
        <v-container class="my-5">
             <v-layout row wrap>
                 <v-flex xs12 sm6 md4 lg3 v-for="category in categories" :key="category.judul">
                     <v-card flat class="text-xs-center ma-3">
                         <v-responsive class="pt-4">
                             <v-img
                                class="white--text align-end"
                                height="200px"
                                src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
                                >
                                <v-card-title>{{ category.penulis}}</v-card-title>
                            </v-img>
                         </v-responsive>
                     </v-card>
                 </v-flex>
             </v-layout>
        </v-container>
    </div>
</template>

<script>
  export default {
    data(){
        return{
            categories:[
                { judul: 'Sejarah sejarah', penulis: 'Anton'},
                { judul: 'Sejarah sejarah', penulis: 'Anton'},
                { judul: 'Sejarah sejarah', penulis: 'Anton'},
            ]
        }
    }
  }
</script>