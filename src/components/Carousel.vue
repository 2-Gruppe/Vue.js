<template lang="">
  <v-carousel
    cycle
    xs12
    sm6
    md4
    lg3
    height="500"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item
      xs12
      sm6
      md4
      lg3
      v-for="item in items"
      :key="item"
      :src="item"
      ><h1
        class=" display-1 my-3 mx-15 font-weight-bold grey--text text--darken-1 my-5 text-left"
      >
        Data ist Macht!
      </h1>

      <h3
        class="display-5 my-3 mx-15  font-weight-bold grey--text text--darken-3 my-5 text-left"
      >
        Wir beleuchten gerne Ihren Weg zum Ziel!
      </h3></v-carousel-item
    >
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
        {
          src: require('../assets/c10.png'),
        },
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
