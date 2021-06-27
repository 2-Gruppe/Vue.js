<template lang="">
  <nav>
    <v-app-bar color="grey lighten-1" elevation="1" dark app flat>
      <v-app-bar-nav-icon id="drawerIcon" @click="drawer = !drawer">
      </v-app-bar-nav-icon>
      <img class="mr-3" :src="require('../assets/analytics.png')" height="35" />
      <v-toolbar-title class=" white--text">
        <span class="font-weight-light">Team</span>
        <strong class=" font-weight-medium">HFH</strong>
        <v-switch
          width="100%"
          class="my-8 mx-1 align-center "
          v-model="$vuetify.theme.dark"
          label="Dunkellll"
          persistent-hint
        ></v-switch>
      </v-toolbar-title>

      <v-flex class="d-flex flex-row mx-auto justify-end" xs12 lg12 md12 sm12>
        <v-btn
          rounded
          elevation="1"
          text
          small
          color="black"
          class="my-5  white--text"
          router
          to="/"
        >
          <v-icon>mdi-home</v-icon>Home</v-btn
        >

        <v-btn
          rounded
          elevation="1"
          text
          small
          color="black"
          class="my-5  white--text"
          router
          to="/Cards"
        >
          <v-icon>mdi-hospital-building</v-icon>Kliniken</v-btn
        >
        <v-btn
          rounded
          elevation="1"
          small
          color="error"
          class="my-5  white--text"
          href="https://fahricigdem.github.io/klinikbewertungen-react/"
          >Experten</v-btn
        >
      </v-flex>
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer" color="grey darken-3">
      <v-layout column align-center>
        <v-flex class="my-5">
          <v-img
            align-center
            max-width="100px"
            class="my-5"
            src="../assets/analytics.png"
          ></v-img>
        </v-flex>
      </v-layout>

      <v-list flat>
        <v-list-item
          v-for="link in links"
          :key="link.route"
          link
          :to="link.route"
          exact="true"
        >
          <v-list-item-icon>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="white--text">{{
              link.text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  data: function() {
    return {
      props: {
        attrs: {
          type: Object,
          default: () => ({}),
        },
      },
      drawer: false,

      links: [
        { icon: 'mdi-home', text: 'Home', route: '/' },

        {
          icon: 'mdi-forum',
          text: 'Kontakt ',
          route: '/Kontakt',
        },

        {
          icon: 'mdi-forum',
          text: 'Über Uns',
          route: '/Uberuns',
        },
      ],
    };
  },
};
</script>

<style scoped></style>
