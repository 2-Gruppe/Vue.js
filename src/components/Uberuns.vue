<template>
  <v-card class="mx-auto" max-width="750">
    <v-container fluid>
      <v-row>
        <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
          <v-card hover>
            <v-img
              :src="card.src"
              class="white--text align-end justify-center"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            >
              <v-card-title v-text="card.title"></v-card-title>
              <v-card-subtitle
                class="orange--text"
                v-text="card.sub"
              ></v-card-subtitle>
            </v-img>
            <v-dialog transition="dialog-bottom-transition" max-width="600">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  class="justify-end"
                  icon
                  color="error"
                  v-bind="attrs"
                  v-on="on"
                  ><v-icon>mdi-account-details-outline</v-icon></v-btn
                >
                <v-btn icon>
                  <v-icon>mdi-github</v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon>mdi-linkedin </v-icon>
                </v-btn>

                <v-btn icon>
                  <v-icon>mdi-xing</v-icon>
                </v-btn>
              </template>
              <template v-slot:default="dialog">
                <v-card>
                  <v-toolbar color="primary" dark
                    >Opening from the bottom</v-toolbar
                  >
                  <v-card-text>
                    <div class="text-h6 pa-12">Hello world!</div>
                  </v-card-text>
                  <v-card-actions class="justify-end">
                    <v-btn text @click="dialog.value = false">Close</v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>

            <v-card-actions>
              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>
<script>
export default {
  data: () => ({
    cards: [
      // {
      //   title: 'Unser Team',
      //   src: require('../assets/team/team3.jpg'),
      //   flex: 12,
      // },
      {
        text: 'asdfghjklwertyuiop',
        sub: 'Data Scientist',
        title: 'Fahri Çiğdem',
        src: 'https://cdn.vuetifyjs.com/images/cards/road.jpg',
        flex: 4,
      },
      {
        text: 'asdfghjklwertyuiop',
        sub: 'Web Entwickler',
        title: 'Hakan Ünlü',
        src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg',
        flex: 4,
      },
      {
        text: 'asdfghjklwertyuiop',
        sub: 'App Entwickler',
        title: 'Hussain',
        src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg',
        flex: 4,
      },
    ],
  }),
};
</script>
