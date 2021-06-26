<template lang="">
  <v-footer elevation="1" height="60" padless>
    <v-card class="flex" dark>
      <v-card-title class="grey lighten-1 " elevation="1">
        <img
          class="mr-3"
          :src="require('../assets/analytics.png')"
          height="40"
        />
        <h6 class="text-subtitle-1 mt-2 text-white font-weight-light ">
          &copy; {{ new Date().getFullYear() }} Team HFH, Verbinden Sie sich mit
          uns in sozialen Netzwerken!
        </h6>

        <v-spacer></v-spacer>

        <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  data: () => ({
    icons: ['mdi-twitter', 'mdi-linkedin', 'mdi-instagram', 'mdi-github'],
  }),
};
</script>
<style scoped></style>
