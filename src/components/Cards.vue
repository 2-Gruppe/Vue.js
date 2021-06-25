<template lang="">
  <v-container fluid class="grey lighten-5">
    <v-row class="mb-3" no-gutters>
      <v-card
        xs12
        sm6
        md4
        lg3
        hover
        v-for="n in KlinikDaten"
        :key="n"
        elevation="10"
        tile
        class="mx-auto my-12 rounded-lg "
        max-width="374"
        :to="n.route"
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

          <div
            class="my-4 text-subtitle-2 font-weight-thin orange--text text--accent-4"
          >
            Durchschnittliche Sterne Bewertung
          </div>

          <div>
            "Wer nicht jeden Tag etwas für seine Gesundheit tut, der muss eines
            Tages sehr viel Zeit für die Krankheit aufbringen."

            <div
              class=" text-subtitle-2 font-weight-thin grey--text text--darken-4"
            >
              Rothkirch, Michael
            </div>
          </div>
        </v-card-text>
        <v-card-actions>
          <v-btn block color="orange lighten-1" elevation="10" :to="n.route">
            <!-- <v-icon color="dark">mdi-magnify</v-icon> -->
            MEHR
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
          sterne: Math.round(4.25),
          review: 113,
          src: require('../assets/Hospitals/herzogin.png'),
          route: '/Herzogin',
        },
        {
          name: 'Klinik am Zuckerberg',
          sterne: Math.round(4),
          review: 38,
          src: require('../assets/Hospitals/Zuckerberg.png'),
          route: '/Klinikzuckerberg',
        },
        {
          name: 'Klinikum Wolfsburg',
          sterne: Math.round(2.77),
          review: 165,
          src: require('../assets/Hospitals/klinikumwolfsburg.png'),
          route: '/Klinikumwolfsburg',
        },
        {
          name: 'Klinikum Peine',
          sterne: Math.round(3),
          review: 105,
          src: require('../assets/Hospitals/Klinikum_Peine_2020.png'),
          route: '/Peine',
        },
        {
          name: 'St. Martini Krankenhaus',
          sterne: Math.round(4.3),
          review: 33,
          src: require('../assets/Hospitals/Martini.png'),
          route: '/Martini',
        },
        {
          name: 'DIAKOVERE Henriettenstift',
          sterne: Math.round(2.98),
          review: 98,
          src: require('../assets/Hospitals/DKH_Aussenansicht-1.png'),
          route: '/Henristift',
        },
        {
          name: 'Eilenriede Klinik Hannover',
          sterne: Math.round(4.83),
          review: 31,
          src: require('../assets/Hospitals/eilenriedeklinik.png'),
          route: '/Ellenriede',
        },
        {
          name: 'Sophienklinik',
          sterne: Math.round(3.85),
          review: 101,
          src: require('../assets/Hospitals/Sophien.png'),
          route: '/Sophien',
        },
        {
          name: 'KRH Klinikum Agness Karll Laatzen',
          sterne: Math.round(2.92),
          review: 109,
          src: require('../assets/Hospitals/Laatzen.png'),
          route: '/Laatzen',
        },
        {
          name: 'Klinikum Wahrendorff',
          sterne: Math.round(3.04),
          review: 22,
          src: require('../assets/Hospitals/Wahrendorff.png'),
          route: '/Wahrendorff',
        },
        {
          name: 'AMEOS Klinikum Hildesheim',
          sterne: 2.5,
          review: 66,
          src: require('../assets/Hospitals/k_helios-klinikum-hildesheim.png'),
          route: '/Hildesheim',
        },
        {
          name: 'Helios Kliniken Mittelweser',
          sterne: Math.round(2.39),
          review: 149,
          src: require('../assets/Hospitals/Helios-Kliniken-Mittelweser.png'),
          route: '/Mittelweser',
        },
        {
          name: 'HELIOS Klinik Cuxhaven',
          sterne: Math.round(2.92),
          review: 122,
          src: require('../assets/Hospitals/HELIOS Klinik Cuxhaven.png'),
          route: '/Cuxhaven',
        },
        {
          name: 'AMEOS Klinikum Seepark Geestland',
          sterne: Math.round(3.29),
          review: 48,
          src: require('../assets/Hospitals/Seepark.png'),
          route: '/Seepark',
        },
        {
          name: 'Krankenhaus Buchholz',
          sterne: Math.round(2.79),
          review: 119,
          src: require('../assets/Hospitals/bucholz.png'),
          route: '/Bucholz',
        },
        {
          name: 'Krankenhaus Winsen',
          sterne: Math.round(3.08),
          review: 150,
          src: require('../assets/Hospitals/Winsen.png'),
          route: '/Winsen',
        },
        {
          name: 'Psychiatrische Klinik Lüneburg',
          sterne: 2.5,
          review: 35,
          src: require('../assets/Hospitals/Luneburg.png'),
          route: '/Luneburg',
        },
      ],
    };
  },
};
</script>
