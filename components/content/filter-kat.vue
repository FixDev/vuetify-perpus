<template>
  <div>
      <v-container>
          <v-row
          align="center"
          justify="center">
              <div>
                <v-btn
                class="mx-1"
                color="info" text>
                {{ nama }}
                </v-btn>
              </div>
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

        nama:{
            type: String,
            default: ''
        },
    },
}
</script>

<style>

</style>