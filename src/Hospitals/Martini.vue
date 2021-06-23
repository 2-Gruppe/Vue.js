<template lang="">
  <v-card elevation="10" tile class="mx-auto my-12 rounded-lg " max-width="374">
    <v-img height="200" src="../assets/Hospitals/Martini.jpg"></v-img>

    <v-card-title>St. Martini Krankenhaus</v-card-title>

    <v-card-text>
      <v-row align="center" class="mx-0">
        <v-rating
          :value="4.5"
          color="amber"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ms-4">
          4.5 (413)
        </div>
      </v-row>

      <div class="my-4 text-subtitle-1">
        $ • Italian, Cafe
      </div>

      <div>
        Small plates, salads & sandwiches - an intimate setting with 12 indoor
        seats plus patio seating.
      </div>
    </v-card-text>
    <v-card-actions>
      <v-btn
        block
        color="orange white--text"
        elevation="10"
        router
        to="/Martini"
      >
        <v-icon color="dark">mdi-binoculars</v-icon>
        MEHR DAZU
      </v-btn>

      <v-spacer></v-spacer>
    </v-card-actions>
    <v-divider class="mx-4"></v-divider>
  </v-card>
</template>

<script>
export default {
  name: 'Kart',
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style scoped></style>
