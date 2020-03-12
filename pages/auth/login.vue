<template>
  <div id="app">
    <v-app
      :class="{ 'pa-3': $vuetify.breakpoint.smAndUp }"
      :dark="darkTheme"
      id="inspire"
    >
      <v-container>
        <v-layout wrap>
          <v-flex sm12 md6 offset-md3>
            <v-card elevation="4" light tag="section">
              <v-card-title>
                <v-layout align-center justify-space-between>
                  <h3 class="headline">
                    {{ platformName }}
                  </h3>
                  <v-flex>
                    <v-img
                      :alt="platformName"
                      class="ml-3"
                      contain
                      height="48px"
                      position="center right"
                      src="https://www.boxfordlibrary.org/wordpress/wp-content/uploads/2014/03/elibrary-logo.png"
                    ></v-img>
                  </v-flex>
                </v-layout>
              </v-card-title>
              <v-divider></v-divider>
              <v-card-text>
                <p>Sign in with your username and password:</p>
                <v-form>
                  <v-text-field
                    outline
                    label="Email"
                    type="text"
                    v-model="email"
                  ></v-text-field>
                  <v-text-field
                    outline
                    hide-details
                    label="Password"
                    type="password"
                    v-model="password"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-divider></v-divider>
              <v-card-actions :class="{ 'pa-3': $vuetify.breakpoint.smAndUp }">
                <v-btn color="info" flat>
                  Forgot password?
                </v-btn>
                <v-spacer></v-spacer>
                <v-btn color="info" :large="$vuetify.breakpoint.smAndUp">
                  Login
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-app>
  </div>
</template>

<script>
export default {
  data() {
    return {
      darkTheme: true,
      platformName: "E-Library",
      password: null,
      email: null
    };
  }
};
</script>

<style>
.v-card {
  border-radius: 4px; 
  }
.v-card__title {
  text-transform: uppercase;
  }
</style>
