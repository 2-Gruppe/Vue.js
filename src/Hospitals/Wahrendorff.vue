<template lang="">
  <v-layout row wrap>
    <v-img height="250" src="../assets/Hospitals/Wahrendorff.jpg"></v-img>
    <br />
    <!-- Klinikbewertungen carousel -->

    <v-card
      elevation="24"
      min-width="374"
      max-width="750"
      class="mx-auto my-12"
      xs12
      sm6
      md4
      lg3
      v-if="show"
    >
      <v-system-bar lights-out> </v-system-bar>
      <v-carousel
        :continuous="true"
        :show-arrows="true"
        hide-delimiter-background
        delimiter-icon="mdi-minus"
        height="450"
      >
        <v-carousel-item
          xs12
          sm6
          md4
          lg3
          v-for="(slide, i) in images"
          :key="i"
          :src="slide.src"
        >
          <strong>
            {{ slide.name }}
          </strong>
        </v-carousel-item>
      </v-carousel>
    </v-card>

    <!-- GoogleMaps carousel -->

    <v-card
      elevation="24"
      min-width="374"
      max-width="750"
      class="mx-auto my-12"
      xs12
      sm6
      md4
      lg3
      v-if="!show"
    >
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
          <strong class="font-weight-bold text-h6 mx-2">
            {{ img.name }}
          </strong>
        </v-carousel-item>
      </v-carousel>
    </v-card>

    <!-- Switch button -->

    <v-col cols="12">
      <storng v-if="!show" class="red--text mx-2 mb-2">GoogleMaps</storng>
      <strong v-if="show" class="green--text mx-2 mb-2"
        >Klinikbewertungen.de</strong
      >
      <v-switch
        class=" mx-2 "
        v-model="show"
        color="grey lighten-1"
        label="Source auswahlen"
      ></v-switch>
    </v-col>

    <!-- Klinikbewertungen data -->

    <v-card
      elevation="10"
      tile
      class=" my-12 rounded-lg "
      xs12
      sm6
      md4
      lg3
      v-if="show"
    >
      <v-card-title>
        Kliniken

        <span class="red--text subtitle-1  mx-7"
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
        :items-per-page="5"
        :headers="headers"
        :items="desserts"
        :search="search"
        class="elevation-1 text-sm-center"
      >
        <template v-slot:item.gesamt="{ item }">
          <v-chip :color="getFarbe(item.gesamt)" dark>
            {{ item.gesamt }}
          </v-chip>
        </template></v-data-table
      >
    </v-card>

    <!-- GoogleMaps data -->

    <v-card
      elevation="10"
      xs12
      sm6
      md4
      lg3
      tile
      class=" my-12 rounded-lg "
      v-if="!show"
    >
      <v-card-title>
        Kliniken

        <span class="red--text subtitle-1  mx-7"
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
        :items-per-page="5"
        :headers="headgoogle"
        :items="google"
        :search="search"
        class="elevation-5 text-sm-center"
      >
        <template v-slot:item.sterne="{ item }">
          <v-chip :color="getColor(item.sterne)" dark>
            {{ item.sterne }}
          </v-chip>
        </template>
      </v-data-table>
    </v-card>
  </v-layout>
</template>
<script>
import kjson from '../assets/klinik by klinik json/Klinikum Wahrendorff_klinikDe.json';
import gjson from '../assets/klinik by klinik json/Klinikum Wahrendorff_googleMaps.json';

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
        { text: 'sterne', value: 'sterne' },
        { text: 'positive', value: 'positive' },
        { text: 'source', value: 'source' },
      ],
      google: gjson,

      images: [
        {
          name: 'FachbereichPolarities ',
          src: require('../images-klinikbewertungen/FachbereichPolarities/FachbereichPolarities_Klinikum Wahrendorff.png'),
        },
        {
          name: 'PolaritiyProJahr',
          src: require('../images-klinikbewertungen/PolaritiyProJahr/PolaritiyProJahr_Klinikum Wahrendorff.png'),
        },
        {
          name: 'KommentareProJahr ',
          src: require('../images-klinikbewertungen/KommentareProJahr/KommentareProJahr_Klinikum Wahrendorff.png'),
        },
        {
          name: 'PositiveNegativeProJahr ',
          src: require('../images-klinikbewertungen/PositiveNegativeProJahr/PositiveNegativeProJahr_Klinikum Wahrendorff.png'),
        },
      ],
      googleimages: [
        {
          name: 'PolaritiyProJahr',
          src: require('../images-google/PolaritiyProJahr/PolaritiyProJahr_Klinikum Wahrendorff_google.png'),
        },
        {
          name: 'KommentareProJahr ',
          src: require('../images-google/KommentareProJahr/KommentareProJahr_Klinikum Wahrendorff_google.png'),
        },
        {
          name: 'PositiveNegativeProJahr ',
          src: require('../images-google/PositiveNegativeProJahr/PositiveNegativeProJahr_Klinikum Wahrendorff_google.png'),
        },
      ],
    };
  },

  methods: {
    getColor(sterne) {
      if (sterne === 5) return 'pink';
      else if (sterne === 4) return 'blue';
      else if (sterne === 3) return 'yellow';
      else if (sterne === 2) return 'orange';
      else if (sterne === 1) return 'green';
    },
    getFarbe(gesamt) {
      if (gesamt === 'sehr zufrieden') return 'green';
      else if (gesamt === 'zufrieden') return 'red';
      else if (gesamt === 'weniger zufrieden') return 'orange';
      else if (gesamt === 'unzufrieden') return 'blue';
    },
  },
};
</script>
<style lang=""></style>
