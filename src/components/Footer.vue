<template lang="">
  <v-footer dark padless>
    <v-card class="flex" flat tile>
      <v-card-title class="orange" dark>
        <strong class="subheading"
          >Get connected with us on social networks!</strong
        >

        <v-spacer></v-spacer>

        <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>

      <v-card-text class="py-2 orange--text text-center" height="10">
        {{ new Date().getFullYear() }} —
        <strong class="buchstabe"
          >TEAM <span class="buchstabe">H</span><span class="buchstabe">F</span
          ><span class="buchstabe">H</span></strong
        >
      </v-card-text>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  name: 'Footer',

  data: () => ({
    icons: ['mdi-twitter', 'mdi-linkedin', 'mdi-instagram', 'mdi-github'],
  }),
};
</script>
<style scoped>
.buchstabe {
  color: orange;
}
</style>
