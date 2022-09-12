<template>
  <v-container fluid>
    <v-row>
      <v-col cols="4" v-for="post in APIData" :key="post.id">
        <v-hover v-slot="{ hover }">
          <v-card class="mx-auto" max-width="344" :elevation="hover ? 15 : 2">
            <v-img :src="getImg(post.thumbnail)" height="200px"> </v-img>
            <v-card-title>{{ post.title }}</v-card-title>
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
        console.log(this.APIData);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
