<template lang="">
  <v-layout row>
    <br />
    <!-- Klinikbewertungen carousel -->

    <v-card
      fill-height
      elevation="24"
      min-width="374"
      max-width="750"
      class="mx-auto my-6"
      xs12
      sm6
      md4
      lg3
      v-if="show"
    >
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
      class="mx-auto my-6"
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
        label="Source auswählen"
      ></v-switch>
    </v-col>

    <!-- Klinikbewertungen data -->

    <v-card
      elevation="10"
      tile
      class=" my-12 rounded-lg  "
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
        :items="klinikdaten"
        :search="search"
        class="elevation-1 text-sm-center "
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
        class="elevation-5 text-sm-center "
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
import kjson from '../assets/klinik by klinik json/Herzogin Elisabeth Hospital_klinikDe.json';
import gjson from '../assets/klinik by klinik json/Herzogin Elisabeth Hospital_googleMaps.json';

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
          align: 'center',
          sortable: true,
          value: 'name',
        },
        { text: 'Titel', value: 'titel' },
        { text: 'Komment', value: 'komment', align: 'start' },
        { text: 'Gesamt', value: 'gesamt' },
        { text: 'Positive', value: 'positive' },
        { text: 'Source', value: 'source' },
      ],
      klinikdaten: kjson,

      headgoogle: [
        {
          text: 'Kliniken',
          align: 'center',
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
    getColor(sterne) {
      if (sterne === 5) return 'success';
      else if (sterne === 4) return 'primary';
      else if (sterne === 3) return 'warning';
      else if (sterne === 2) return 'yellow';
      else if (sterne === 1) return 'error';
    },
    getFarbe(gesamt) {
      if (gesamt === 'sehr zufrieden') return 'success';
      else if (gesamt === 'zufrieden') return 'primary';
      else if (gesamt === 'weniger zufrieden') return 'warning';
      else if (gesamt === 'unzufrieden') return 'error';
    },
  },
};
</script>
