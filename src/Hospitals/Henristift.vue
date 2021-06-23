<template lang="">
  <v-container fluid>
    <v-row class="mb-6" no-gutters>
      <v-img max-height="300" src="../assets/Hospitals/herzogin.jpg"></v-img>
    </v-row>
    <span class="green--text subtitle-1 mb-2">Klinikbewertungen</span
    ><span class="red--text subtitle-1 mb-2">Google</span>

    <v-switch v-model="show" :label="klinikbewertungen"></v-switch>
    <v-row class="mb-6" no-gutters>
      <v-col cols="8" class="fill-height" height="400">
        <v-spacer></v-spacer>

        <v-card elevation="1" tile class=" my-12 rounded-lg " v-if="show">
          <v-card-title>
            Kliniken
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
        <v-spacer></v-spacer>
        <v-card v-if="!show">
          <v-card-title>
            Kliniken
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
      </v-col>
      <v-divider></v-divider>
      <v-col cols="4" v-if="show">
        <v-card elevation="10" tile class="mx-auto my-12 rounded-lg ">
          <v-img
            :aspect-ratio="16 / 9"
            v-for="image in images"
            :key="image"
            :src="image"
            class="elevation-1"
          >
            <v-divider></v-divider>
            <p class="text-subtitle-4 text-xl-left">
              {{ image.name }}
            </p>
          </v-img>
        </v-card>
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
      if (gesamt === 'Sehr zufrieden') return 'green';
      else if (gesamt == 67) return 'blue';
      else if (gesamt == 33) return 'orange';
      else return 'red';
    },
    handleSourceClick() {},
  },
};
</script>
<style lang=""></style>
