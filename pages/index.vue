<template>
  <div>
    <v-system-bar status color="primary" class="white--text px-5">
      <div>BOOM HR</div>
      <v-spacer></v-spacer>
      <nuxt-link to="/Login" class="tdn white--text">
        <div>SIGN IN</div>
      </nuxt-link>
    </v-system-bar>
    <v-layout class="px-5 py-3 grey lighten-5">BOOM HR LOGO</v-layout>
    <div class="bg">ASasASSas</div>
  </div>
</template>

<style lang="stylus" scoped>
  .bg {
    /* The image used */
    background-image: url("/creative_process/11.jpeg");

    /* Full height */
    height: 500px; 

    /* Center and scale the image nicely */
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  .tdn {
    text-decoration: none;
  }
</style>
  