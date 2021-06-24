<template lang="">
  <v-container fluid class="grey lighten-5">
    <v-row class="mb-3" no-gutters>
      <v-card
        v-for="n in KlinikDaten"
        :key="n"
        elevation="10"
        tile
        class="mx-auto my-12 rounded-lg "
        max-width="374"
      >
        <v-img height="200" :src="n.src"></v-img>

        <v-card-title>{{ n.name }}</v-card-title>

        <v-card-text>
          <v-row align="center" class="mx-0">
            <v-rating
              :value="n.sterne"
              color="amber"
              dense
              half-increments
              readonly
              size="14"
            ></v-rating>

            <div class="grey--text ms-4">{{ n.sterne }} ({{ n.review }})</div>
          </v-row>

          <div class="my-4 text-subtitle-1">
            $ • Italian, Cafe
          </div>

          <div>
            Small plates, salads & sandwiches - an intimate setting with 12
            indoor seats plus patio seating.
          </div>
        </v-card-text>
        <v-card-actions>
          <v-btn block color="orange white--text" elevation="10" :to="n.route">
            <v-icon color="dark">mdi-binoculars</v-icon>
            MEHR DAZU
          </v-btn>

          <v-spacer></v-spacer>
        </v-card-actions>
        <v-divider class="mx-4"></v-divider>
      </v-card>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      show: false,

      KlinikDaten: [
        {
          name: 'Herzogin Elisabeth Hospital',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/herzogin.jpg'),
          route: '/Herzogin',
        },
        {
          name: 'Klinik am Zuckerberg',
          sterne: 5,
          review: 333,
          src: require('../assets/Hospitals/Zuckerberg.jpg'),
          route: '/Klinikzuckerberg',
        },
        {
          name: 'Klinikum Wolfsburg',
          sterne: 3,
          review: 222,
          src: require('../assets/Hospitals/klinikumwolfsburg.jpg'),
          route: '/Klinikumwolfsburg',
        },
        {
          name: 'Klinikum Peine',
          sterne: 1,
          review: 777,
          src: require('../assets/Hospitals/Klinikum_Peine_2020.jpg'),
          route: '/Peine',
        },
        {
          name: 'St. Martini Krankenhaus',
          sterne: 3,
          review: 444,
          src: require('../assets/Hospitals/Martini.jpg'),
          route: '/Martini',
        },
        {
          name: 'DIAKOVERE Henriettenstift',
          sterne: 5,
          review: 444,
          src: require('../assets/Hospitals/DKH_Aussenansicht-1.jpg'),
          route: '/Henristift',
        },
        {
          name: 'Eilenriede Klinik Hannover',
          sterne: 1,
          review: 444,
          src: require('../assets/Hospitals/eilenriedeklinik.jpg'),
          route: '/Ellenriede',
        },
        {
          name: 'Sophienklinik',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Sophien.jpg'),
          route: '/Sophien',
        },
        {
          name: 'KRH Klinikum Agness Karll Laatzen',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Laatzen.jpg'),
          route: '/Laatzen',
        },
        {
          name: 'Klinikum Wahrendorff',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Wahrendorff.jpg'),
          route: '/Wahrendorff',
        },
        {
          name: 'AMEOS Klinikum Hildesheim',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/k_helios-klinikum-hildesheim.png'),
          route: '/Hildesheim',
        },
        {
          name: 'Helios Kliniken Mittelweser',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Helios-Kliniken-Mittelweser.jpg'),
          route: '/Mittelweser',
        },
        {
          name: 'HELIOS Klinik Cuxhaven',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/HELIOS Klinik Cuxhaven.jpg'),
          route: '/Cuxhaven',
        },
        {
          name: 'AMEOS Klinikum Seepark Geestland',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Seepark.jpg'),
          route: '/Seepark',
        },
        {
          name: 'Krankenhaus Buchholz',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/bucholz.jpg'),
          route: '/Bucholz',
        },
        {
          name: 'Krankenhaus Winsen',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Winsen.jpg'),
          route: '/Winsen',
        },
        {
          name: 'Psychiatrische Klinik Lüneburg',
          sterne: 4,
          review: 444,
          src: require('../assets/Hospitals/Luneburg.jpeg'),
          route: '/Luneburg',
        },
      ],
    };
  },
};
</script>
