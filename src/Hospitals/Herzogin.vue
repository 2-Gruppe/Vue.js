<template lang="">
  <v-container fluid>
    <v-row class="mb-6" no-gutters>
      <v-img max-height="300" src="../assets/Hospitals/herzogin.jpg"></v-img>
    </v-row>
    <span class="red--text subtitle-1 mb-2">Google</span>
    <span class="green--text subtitle-1 mb-2">Klinikbewertungen</span>

    <v-switch
      v-model="show"
      :label="Klinikbewertungen"
      color="orange"
    ></v-switch>
    <v-row class="mb-6" no-gutters>
      <v-col cols="8" class="fill-height" height="400">
        <v-spacer></v-spacer>

        <v-card elevation="1" tile class=" my-12 rounded-lg " v-if="show">
          <v-card-title>
            Kliniken
            <v-divider></v-divider>
            <span class="red--text subtitle-1 mb-2"
              >{{ kjson.length }} Bewertungen gefunden</span
            >
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
            dense
            :items-per-page="6"
            :headers="headers"
            :items="desserts"
            :search="search"
            class="elevation-1 text-sm-center"
          >
            <template v-slot:item.group="{ item }">
              <v-chip :color="getColor(item.group)" dark>
                {{ item.group }}
              </v-chip>
            </template>
            <template v-slot:item.gesamt="{ item }">
              <v-chip :color="getFarbe(item.gesamt)" dark>
                {{ item.gesamt }}
              </v-chip>
            </template></v-data-table
          >
        </v-card>
        <v-spacer></v-spacer>
        <v-card v-if="!show">
          <v-card-title>
            Kliniken
            <v-divider></v-divider>
            <span class="red--text subtitle-1 mb-2"
              >{{ gjson.length }} Bewertungen gefunden</span
            >
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
            dense
            :items-per-page="10"
            :headers="headgoogle"
            :items="google"
            :search="search"
            class="elevation-5 text-sm-center"
          >
          </v-data-table>
        </v-card>
      </v-col>
      <v-divider></v-divider>
      <v-col cols="4" v-if="show">
        <v-flex xs12 sm6 md3 lg3 v-for="image in images" :key="image">
          <v-card hover class="ma-4" min-height="400" min-width="400">
            <v-layout column align-center fill-height class="text-center">
              <v-img :src="image"></v-img>

              <v-card-title class="font-weight-light">{{
                image.name
              }}</v-card-title>
              <v-spacer></v-spacer>

              <v-card-text> </v-card-text>
            </v-layout>
          </v-card>
        </v-flex>
      </v-col>
      <v-col cols="4" v-if="!show">
        <v-flex xs12 sm6 md3 lg3 v-for="img in googleimages" :key="img">
          <v-card hover class="ma-4" min-height="400" min-width="400">
            <v-layout column align-center fill-height class="text-center">
              <v-img :src="img"></v-img>

              <v-card-title class="font-weight-light">{{
                img.name
              }}</v-card-title>
              <v-spacer></v-spacer>

              <v-card-text> </v-card-text>
            </v-layout>
          </v-card>
        </v-flex>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import kjson from '../assets/Herzogin Elisabeth Hospital_klinikDe.json';
import gjson from '../assets/Herzogin Elisabeth Hospital_googleMaps.json';

export default {
  data() {
    return {
      search: '',
      page: 1,
      kjson,
      gjson,
      show: true,

      headers: [
        {
          text: 'Kliniken',
          align: 'start',
          sortable: true,
          value: 'name',
        },
        { text: 'titel', value: 'titel' },
        { text: 'komment', value: 'komment' },
        { text: 'gesamt', value: 'gesamt' },
        { text: 'positive', value: 'positive' },
        { text: 'source', value: 'source' },
      ],
      desserts: kjson,
      headgoogle: [
        {
          text: 'Kliniken',
          align: 'start',
          sortable: true,
          value: 'name',
        },

        { text: 'komment', value: 'komment' },
        { text: 'gesamt', value: 'gesamt' },
        { text: 'positive', value: 'positive' },
        { text: 'source', value: 'source' },
      ],
      google: gjson,

      images: [
        {
          name: 'FachbereichPolarities ',
          src: require('../images-klinikbewertungen/FachbereichPolarities/FachbereichPolarities_Herzogin Elisabeth Hospital.png'),
        },
        {
          name: 'PolaritiyProJahr',
          src: require('../images-klinikbewertungen/PolaritiyProJahr/PolaritiyProJahr_Herzogin Elisabeth Hospital.png'),
        },
        {
          name: 'KommentareProJahr ',
          src: require('../images-klinikbewertungen/KommentareProJahr/KommentareProJahr_Herzogin Elisabeth Hospital.png'),
        },
        {
          name: 'PositiveNegativeProJahr ',
          src: require('../images-klinikbewertungen/PositiveNegativeProJahr/PositiveNegativeProJahr_Herzogin Elisabeth Hospital.png'),
        },
      ],
      googleimages: [
        {
          name: 'PolaritiyProJahr',
          src: require('../images-google/PolaritiyProJahr/PolaritiyProJahr_Herzogin Elisabeth Hospital_google.png'),
        },
        {
          name: 'KommentareProJahr ',
          src: require('../images-google/KommentareProJahr/KommentareProJahr_Herzogin Elisabeth Hospital_google.png'),
        },
        {
          name: 'PositiveNegativeProJahr ',
          src: require('../images-google/PositiveNegativeProJahr/PositiveNegativeProJahr_Herzogin Elisabeth Hospital_google.png'),
        },
      ],
    };
  },

  methods: {
    getColor(group) {
      if (group == 4) return 'green';
      else if (group == 3) return 'blue';
      else if (group == 2) return 'orange';
      else return 'red';
    },
    getFarbe(gesamt) {
      if (gesamt === 100) return 'green';
      else if (gesamt == 67) return 'blue';
      else if (gesamt == 33) return 'orange';
      else return 'red';
    },
  },
};
</script>
<style lang=""></style>
