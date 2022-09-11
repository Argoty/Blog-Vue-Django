<template>
  <v-container>
    <v-col class="d-flex justify-center">
      <router-link to="/" class="rutas blog">
        Blog
        <v-icon color="brown darken-2">mdi-post</v-icon>
      </router-link>
      |
      <router-link to="/about" class="rutas about">
        About
        <v-icon color="brown darken-2">mdi-information-outline</v-icon>
      </router-link>
    </v-col>
  </v-container>
</template>

<script>
export default {
  name: "Rutas",
};
</script>

<style scoped>
.rutas {
  text-decoration: none;
  color: #5D4037;
  font-weight: bold;
  font-family: "Segoe UI";
  font-size: 20px;
}
.rutas:hover {
  color: #825b4f;
}
.blog {
  margin-right: 5px;
}
.about {
  margin-left: 5px;
}
</style>

