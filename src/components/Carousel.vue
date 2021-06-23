<template lang="">
  <v-carousel height="460" hide-delimiter-background show-arrows-on-hover>
    <v-carousel-item v-for="item in items" :key="item" :src="item"
      ><h1
        class="text-decoration-underline display-1 my-3 mx-15 font-weight-bold red--text my-5 text-left"
      >
        Data ist Macht!
      </h1>

      <h3
        class="display-5 my-3 mx-15  font-weight-bold white--text my-5 text-left"
      >
        Nur beleuchten wir gerne Ihren Weg zum Ziel
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
          src: require('../assets/key-2114046_1280.jpg'),
        },
        {
          src: require('../assets/c9.jpg'),
        },
        {
          src: require('../assets/c10.jpg'),
        },
        {
          src: require('../assets/c3.jpg'),
        },

        {
          src: require('../assets/newton-s-cradle-balls-sphere-action-60582.jpeg'),
        },
      ],
    };
  },
};
</script>
<style lang=""></style>
