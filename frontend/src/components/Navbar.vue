<template>
  <v-app-bar app color="brown darken-2" dark>
    <div class="d-flex align-center">
      <v-img
        alt="Blog Logo"
        class="shrink mr-2"
        contain
        src="../assets/blog.png"
        transition="scale-transition"
        width="40"
      />

      <h1>Blog</h1>
    </div>

    <v-spacer></v-spacer>

    <v-btn
      href="https://github.com/JaxisArty/Blog-Vue-Django"
      target="_blank"
      text
    >
      <span class="mr-2">Project Code</span>
      <v-icon>mdi-open-in-new</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  name: "Navbar",
};
</script>