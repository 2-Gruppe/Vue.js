<template lang="">
  <v-row>
    <v-col cols="12" sm="12" class="justify-center elevation-1">
      <v-data-table
        :headers="headers"
        :items="desserts"
        :items-per-page="3"
        class="elevation-1"
      ></v-data-table>
    </v-col>
  </v-row>
</template>
<script>
import json from '../assets/data.json';
export default {
  data() {
    return {
      headers: [
        {
          text: 'Klinikum',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'name', value: 'name' },
        { text: 'komment', value: 'komment' },
        { text: 'gesamt', value: 'gesamt' },
        { text: 'likes', value: 'likes' },
        { text: 'sterne', value: 'sterne' },
      ],
      desserts: json,
    };
  },
};
</script>
