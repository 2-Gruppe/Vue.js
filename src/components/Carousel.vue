<template lang="">
  <v-carousel
    cycle
    xs12
    sm6
    md4
    lg3
    height="500"
    hide-delimiter-background
    :show-arrows="true"
  >
    <v-carousel-item
      xs12
      sm6
      md4
      lg3
      v-for="item in items"
      :key="item"
      :src="item"
    >
      <h1
        class=" display-5  mx-15 font-weight-thin error--text text--darken-4 my-5 text-left align-center font-italic"
      >
        Daten sind das Öl des 21. Jahrhunderts
      </h1>
    </v-carousel-item>
  </v-carousel>
</template>
<script>
export default {
  data() {
    return {
      items: [
        {
          src: require('../assets/key-2114046_1280.png'),
        },
        {
          src: require('../assets/c9.png'),
        },
        // {
        //   src: require('../assets/c10.png'),
        // },
        {
          src: require('../assets/data1.jpg'),
        },

        {
          src: require('../assets/data4.png'),
        },
      ],
    };
  },
};
</script>
<style lang=""></style>
