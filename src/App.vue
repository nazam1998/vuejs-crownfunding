<template>
  <div id="app">
    <NavBar />
    <div
      :style="{ backgroundImage: 'url(' + imgSrc + ')' }"
      class="bg-header"
    ></div>
    <Title :project="project" />
    <Progress :project="project" />
    <About :project="project" />
    <Modal v-if="showModal" :project="project" />
    <SuccessModal v-if="showSuccessModal" />
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";
import Title from "@/components/Title";
import Progress from "@/components/Progress";
import About from "@/components/About";
import Modal from "@/components/Modal";
import SuccessModal from "@/components/SuccessModal";

import data from "@/assets/data.json";
export default {
  name: "App",
  components: {
    NavBar,
    Title,
    Progress,
    About,
    Modal,
    SuccessModal,
  },
  data() {
    return {
      project: data[0],
      showModal: false,
      showSuccessModal: false,
    };
  },
  mounted() {
    this.imgSrc = require("@/assets/" + this.project.image);
    this.$root.$on("bookmark", this.bookmark);
    this.$root.$on("addFunds", this.addFunds);
    this.$root.$on("change-modal", this.displayModal);
    this.$root.$on("change-success-modal", this.successModal);
  },
  methods: {
    bookmark: function () {
      this.project.bookmarked = !this.project.bookmarked;
      console.log(this.project.bookmarked);
    },
    displayModal: function () {
      this.showModal = !this.showModal;
      if (this.showModal) {
        document.body.overflow = "hidden";
      } else {
        document.body.overflow = "";
      }
    },
    successModal: function () {
      this.showSuccessModal = !this.showSuccessModal;
      if (this.showSuccessModal) {
        document.body.overflow = "hidden";
      } else {
        document.body.overflow = "";
      }
    },
    addFunds(value) {
      console.log(value);
      let choosedPledge = value[0];
      // let pledge = this.project.pledge
      let add = value[1];
      let index = value[2];
      this.$set(this.project, "current", this.project.current + add);
      this.$set(this.project, "backers", this.project.backers + 1);
      if (choosedPledge != "None") {
        this.$set(
          this.project.pledges[index],
          "left",
          this.project.pledges[index].left - 1
        );
      }

      console.log(choosedPledge);
      this.displayModal();
      this.successModal();
    },
  },
  computed: {
    imgSrc: {
      get: function () {
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
