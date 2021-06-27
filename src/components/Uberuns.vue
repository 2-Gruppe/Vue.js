<template>
  <v-container row wrap>
    <v-flex xs12 sm6 md4 lg4 v-for="card in cards" :key="card">
      <v-card hover class="ma-3" justify-center>
        <v-layout column align-center fill-height class="text-center ">
          <v-img :src="card"></v-img>

          <v-card-title class="font-weight-light">{{
            card.title
          }}</v-card-title>
          <v-card-text align-center>
            <v-btn
              v-for="icon in icons"
              :key="icon"
              class="mx-4 "
              color="grey darken-3"
              icon
            >
              <v-icon size="24px">
                {{ icon }}
              </v-icon>
            </v-btn>
          </v-card-text>
          <v-spacer></v-spacer>

          <v-card-text>
            <v-expansion-panels focusable>
              <v-expansion-panel id="synopsis">
                <v-expansion-panel-header color="red lighten-1">{{
                  card.sub
                }}</v-expansion-panel-header>
                <v-expansion-panel-content>{{
                  card.text
                }}</v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-card-text>
        </v-layout>
      </v-card>
    </v-flex>
  </v-container>
</template>
<script>
export default {
  data: () => ({
    icons: ['mdi-twitter', 'mdi-linkedin', 'mdi-xing', 'mdi-github'],
    cards: [
      {
        icon: 'mdi-xing',
        text:
          'Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl',
        src: require('../assets/team/team3.jpg'),
        sub: 'Data Scientist',
        title: 'Fahri Çiğdem',
      },

      {
        icon: 'mdi-linkedin',
        text:
          'Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl',
        sub: 'Web Entwickler',
        title: 'Hakan Ünlü',
        src: require('../assets/team/team3.jpg'),
      },
      {
        icon: 'mdi-github',
        text:
          'Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl Lorem ipsum carrots enhanced rebates. Most flexibl',
        sub: 'App Entwickler',
        title: 'Hussain',
        src: require('../assets/team/team3.jpg'),
      },
    ],
  }),
};
</script>
