<template>
  <v-container>
    <v-img
      :src="getImg($route.params.thumbnail)"
      :lazy-src="getImg($route.params.thumbnail)"
      max-height="300px"

    >
      <template v-slot:placeholder>
        <v-row class="fill-height ma-0 align-center" justify="center">
          <v-progress-circular
            indeterminate
            color="grey lighten-5"
          ></v-progress-circular>
        </v-row>
      </template>
    </v-img>
    <h4 class="text-h4 text-center font-italic">{{ $route.params.title }}</h4>

    <div class="text-body-2 mt-5 text-center">
      <p>
        <b>Author: </b>
        {{
          $route.params.author == 1 ? "Javier Leonardo Argoty Roa" : "Random"
        }}
      </p>
      <p>
        <b >Excerpt: </b> <br />
        {{ $route.params.excerpt }}
      </p>
      <p>
        <b >Content: </b> <br />
        {{ $route.params.content }}
      </p>
      <p>
        <b >Published: </b> <br />
        {{ formatDate($route.params.published) }}
      </p>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "PostDetail",
  methods: {
    getImg(filename) {
      let img = require("../../../backend" + filename);
      return img;
    },
    formatDate(date) {
        let fecha = new Date(date);
        return fecha.toLocaleString()  
    }
  },
};
</script>