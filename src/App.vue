<template>
  <div id="app">
    <NavBar />
    <div
      :style="{ backgroundImage: 'url(' + imgSrc + ')' }"
      class="bg-header"
    ></div>
    <Title :project="project" />
    <Progress />
    <About />
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";
import Title from "@/components/Title";
import Progress from "@/components/Progress";
import About from "@/components/About";
import data from "@/assets/data.json";
export default {
  name: "App",
  components: {
    NavBar,
    Title,
    Progress,
    About,
  },
  data() {
    return {
      project: data[0],
    };
  },
  mounted() {
    this.imgSrc = require("@/assets/" + this.project.image);
    this.$root.$on("bookmark", this.bookmark);
  },
  methods: {
    bookmark: function () {
      this.project.bookmarked = !this.project.bookmarked;
      console.log(this.project.bookmarked);
    },
  },
  computed: {
    imgSrc: {
      get: function () {
        // console.log(this.project);
        return require("@/assets/" + this.project.image);
      },
      set: function () {
        return require("@/assets/" + this.project.image);
      },
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Commissioner&display=swap");
@import "~bootstrap/dist/css/bootstrap.css";

html,
body,
#app {
  height: 100%;
}
#app {
  font-family: "Commissioner", sans-serif;
  font-size: 16px;
}
.bg-header {
  background-image: url("~@/assets/image-hero-desktop.jpg");
  background-size: cover;
  height: 370px;
}
</style>
