<template>
  <v-container fluid>
    <v-row v-if="!dataObtenida">
      <v-col cols="4" v-for="i in cantidadLoaderCards" :key="i">
        <v-skeleton-loader
          class="mx-auto mb-5"
          max-width="350"
          type="image, article"
        ></v-skeleton-loader>
      </v-col>
    </v-row>

    
    <v-row v-else>
      <v-col cols="4" v-for="post in APIData" :key="post.id" >
        <v-hover v-slot="{ hover }">
          <v-card
            class="mx-auto mb-5"
            max-width="350"
            :elevation="hover ? 15 : 2"
          >
            <v-img
              :src="getImg(post.thumbnail)"
              :lazy-src="getImg(post.thumbnail)"
              height="200px"
            >
              <template v-slot:placeholder>
                <v-row class="fill-height ma-0 align-center" justify="center">
                  <v-progress-circular
                    indeterminate
                    color="grey lighten-5"
                  ></v-progress-circular>
                </v-row> </template
            ></v-img>
            <v-card-title>
              <router-link :to="{name: 'PostDetail', params: {...post}}" class="rutaDetail">{{ post.title }}</router-link>
            </v-card-title>
            <v-card-subtitle>{{
              post.author == 1 ? "Javier Argoty" : "Random"
            }}</v-card-subtitle>

            <v-card-text>{{ post.excerpt }}</v-card-text>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { getAPI } from "../axios-api";

export default {
  name: "Blog",
  data() {
    return {
      APIData: [],
      dataObtenida: false,
      cantidadLoaderCards: 4,
    };
  },

  methods: {
    getImg(filename) {
      let img = require("../../../backend" + filename);
      return img;
    },
  },
  created() {
    getAPI
      .get("/blog/posts/")
      .then((response) => {
        console.log("Post API has recieved data");
        this.APIData = response.data.reverse();
        this.dataObtenida = true,
        console.log(this.APIData);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style scoped>
  .rutaDetail {
    text-decoration: none;
    color: #5D4037;
    font-weight: bold;
    font-family: "Segoe UI";
    font-size: 20px;
  }
  .rutaDetail:hover {
    color: #825b4f;
  }
  </style>
