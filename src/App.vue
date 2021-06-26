<template lang="">
  <v-app>
    <Navbar />

    <v-content>
      <router-view></router-view>
      <router-view name="Cards"></router-view>
    </v-content>
    <Footer />
    <!-- <Ornek /> -->
  </v-app>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';
// import Ornek from './Hospitals/Ornek.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    Footer,
    // Ornek,
  },
};
</script>
