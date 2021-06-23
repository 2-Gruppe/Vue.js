<template lang="">
  <v-layout row wrap>
    <v-img max-height="300" src="../assets/Hospitals/bucholz.jpg"></v-img>
    <br />
    <!-- Klinikbewertungen carousel -->

    <v-card elevation="24" width="750" class="mx-auto rounded-lg" v-if="show">
      <v-system-bar lights-out> </v-system-bar>
      <v-carousel
        :continuous="true"
        :show-arrows="true"
        hide-delimiter-background
        delimiter-icon="mdi-minus"
        height="450"
      >
        <v-carousel-item v-for="(slide, i) in images" :key="i" :src="slide.src">
          <strong>
            {{ slide.name }}
          </strong>
        </v-carousel-item>
      </v-carousel>
    </v-card>

    <!-- GoogleMaps carousel -->

    <v-card elevation="24" width="750" class="mx-auto rounded-lg" v-if="!show">
      <v-system-bar lights-out> </v-system-bar>

      <v-carousel
        :continuous="true"
        :show-arrows="true"
        hide-delimiter-background
        delimiter-icon="mdi-minus"
        height="450"
      >
        <v-carousel-item
          v-for="(img, i) in googleimages"
          :key="i"
          :src="img.src"
        >
          <strong class="font-weight-bold">
            {{ img.name }}
          </strong>
        </v-carousel-item>
      </v-carousel>
    </v-card>

    <!-- Switch button -->

    <v-col cols="12" height="10">
      <span class="red--text subtitle-1 mb-2">GoogleMaps</span>
      <span class="green--text subtitle-1 mb-2">Klinikbewertungen.de</span>
      <v-switch
        v-model="show"
        :label="Klinikbewertungen"
        color="orange"
      ></v-switch>
    </v-col>

    <!-- Klinikbewertungen data -->

    <v-card elevation="10" tile class=" my-12 rounded-lg " v-if="show">
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
        :items-per-page="4"
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

    <!-- GoogleMaps data -->

    <v-card elevation="10" tile class=" my-12 rounded-lg " v-if="!show">
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
        :items-per-page="4"
        :headers="headgoogle"
        :items="google"
        :search="search"
        class="elevation-5 text-sm-center"
      >
      </v-data-table>
    </v-card>
  </v-layout>
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
