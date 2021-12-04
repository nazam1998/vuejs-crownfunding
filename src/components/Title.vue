<template>
  <div class="crownfund">
    <div class="card mx-auto w-75 section-title p-4">
      <img
        class="img-mastercraft"
        :src="require('@/assets/logo-mastercraft.svg')"
        alt=""
      />
      <div class="section-text text-center">
        <h3>{{ project.name }}</h3>
        <h5 class="text-muted mt-4">
          A beautiful & handcrafted monitor stand to reduce neck and eye strain.
        </h5>
      </div>
      <div class="section-button mt-5 row justify-content-between">
        <div class="col-4 text-center">
          <button class="btn-back">Back this project</button>
        </div>
        <div class="col-4 text-center">
          <button
            @click="bookmark"
            :class="{
              'btn-bookmarked': project.bookmarked,
              'btn-book': !project.bookmarked,
            }"
          >
            <img :src="bookmarkedImg" class="me-2" alt="" />Bookmark
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Title",
  props: {
    project: Object,
  },
  methods: {
    bookmark: function () {
      this.$root.$emit("bookmark", this.project.bookmarked);
    },
  },
    computed:{
      bookmarkedImg: function () {
        if (this.project.bookmarked){
          return require('@/assets/icon-bookmarked.svg');
        }else{
          return require('@/assets/icon-bookmark.svg');

        }
      }
    },
};
</script>
<style>
.crownfund {
  position: relative;
  top: -100px;
  margin: 0 auto;
}
.img-mastercraft {
  height: 50px;
  width: 50px;
  margin: 0 auto;
  position: relative;
  top: -46px;
}
.section-title h3 {
  font-weight: 1000;
}
.btn-back {
  border-radius: 40px;
  padding: 10px 20px;
  background-color: #3cb4ab;
  color: white;
  border: none;
}
.btn-book {
  border-radius: 40px;
  padding: 0px 20px 0px 0px;
  border: none;
  background-color: rgba(0, 0, 0, 0.07);
}
.btn-bookmarked {
  background-color: rgba(0, 0, 0, 0.07);
  border-radius: 40px;
  padding: 0px 20px 0px 0px;
  border: none;
  color: #3cb4ab;
}
.btn-bookmarked img {
  background-color: #3cb4ab;
  border-radius: 50%;
  color: #3cb4ab;
}
</style>