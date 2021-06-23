<template lang="">
  <nav>
    <v-app-bar color="grey lighten-1" dark flat padless fixed dense>
      <v-app-bar-nav-icon
        id="drawerIcon"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-icon size="24px">
        mdi-code-json
      </v-icon>
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
        to="/Carousel"
      >
        <v-icon>mdi-home</v-icon>Home</v-btn
      >

      <!-- <v-spacer></v-spacer> -->
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
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer" color="grey darken-3">
      <v-layout column align-center>
        <v-flex class="my-5">
          <v-img max-width="100px" src="../assets/home.jpg"></v-img>
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
      drawer: false,
      group: null,
      links: [
        { icon: 'mdi-home', text: 'Home', route: '/' },
        {
          icon: 'mdi-information-variant',
          text: 'Alle Daten',
          route: '/Data',
        },
        {
          icon: 'mdi-trophy',
          text: 'Top Rated ',
          route: '/top-rated-movies',
        },
        {
          icon: 'mdi-television-classic',
          text: 'Popular',
          route: '/popular-shows',
        },
        {
          icon: 'mdi-medal',
          text: 'Top Rated ',
          route: '/top-rated-shows',
        },
        {
          icon: 'mdi-information',
          text: 'Über Uns',
          route: '/Uberuns',
        },
      ],
    };
  },
};
</script>

<style scoped></style>
