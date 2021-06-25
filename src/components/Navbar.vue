<template lang="">
  <nav>
    <v-app-bar color="grey lighten-1" elevation="1" dark dense fixed>
      <v-app-bar-nav-icon id="drawerIcon" @click="drawer = !drawer">
      </v-app-bar-nav-icon>
      <img class="mr-3" :src="require('../assets/analytics.png')" height="35" />
      <v-toolbar-title class=" white--text">
        <span class="font-weight-light">Team</span>
        <strong>HFH</strong>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        icon
        rounded
        elevation="1"
        text
        small
        color="black"
        min-width="100"
        class="my-5 mx-5 white--text"
        router
        to="/"
      >
        <v-icon>mdi-home</v-icon>Home</v-btn
      >

      <v-btn
        elevation="1"
        icon
        rounded
        text
        small
        color="black"
        min-width="100"
        class="my-5 mx-auto white--text"
        router
        to="/Cards"
      >
        <v-icon>mdi-hospital-building</v-icon>Kliniken</v-btn
      >
      <v-btn
        elevation="1"
        rounded
        small
        color="error"
        min-width="100"
        class="my-5 ml-3 white--text"
        href="https://fahricigdem.github.io/klinikbewertungen-react/"
        >Für die Experten</v-btn
      >
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer" color="grey darken-3">
      <v-flex class="my-5">
        <v-img
          max-width="100px"
          class="my-5"
          src="../assets/analytics.png"
        ></v-img>
      </v-flex>

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
      drawer: false,
      group: null,
      source: 'https://fahricigdem.github.io/klinikbewertungen-react/',
      links: [
        { icon: 'mdi-home', text: 'Home', route: '/' },

        {
          icon: 'mdi-forum',
          text: 'Kontakt ',
          route: '/top-rated-movies',
        },
        {
          icon: 'mdi-account-supervisor ',
          text: 'Über Uns',
          route: '/popular-shows',
        },

        {
          icon: 'mdi-forum',
          text: 'Beste Kliniken',
          route: '/Uberuns',
        },
      ],
    };
  },
};
</script>

<style scoped></style>
