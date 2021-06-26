<template lang="">
  <v-footer color="success darken-4" elevation="1" height="60" padless>
    <v-card class="flex">
      <v-card-title class="grey lighten-1 " elevation="1" dark>
        <p class="overline ">
          TEAM HFH - {{ new Date().getFullYear() }}
          Get connected with us on social networks!
        </p>

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
