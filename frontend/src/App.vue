<template>
  <v-app>
    <Navbar />

    <v-main>
      <Rutas />
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar";
import Rutas from "./components/Rutas";

export default {
  name: 'App',
  components: {
    Navbar,
    Rutas
  },

  data: () => ({
    //
  }),
};
</script>
