<template>
  <div class="progress-section">
    <div class="card w-75 mx-auto my-4">
      <div class="section-info">
        <div class="row justify-content-between">
          <div class="col-4">
            <h1>{{showCurrentCurrency}}</h1>
            <p class="text-muted">of {{showMaxCurrency}} backed</p>
          </div>
          <div class="col-4">
            <h1>{{project.backers}}</h1>
            <p class="text-muted">total backers</p>
          </div>
          <div class="col-4">
            <h1>{{ daysLeft }}</h1>
            <p class="text-muted">days left</p>
          </div>
        </div>
        <div class="progress mt-5 border-rounded">
          <div
            class="progress-bar"
            role="progressbar"
            :style="{
              width: currentProgress,
              'border-radius': '10px',
              'background-color': '#3bb4ad',
            }"
            :aria-valuenow="project.current"
            aria-valuemin="0"
            :aria-valuemax="project.max"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Progress",
  props: {
    project: Object,
  },
  computed: {
    currentProgress: function () {
      return (this.project.current / this.project.max) * 100 + "%";
    },
    daysLeft: function () {
      let now = new Date();
      let splitDL = this.project.deadline.split("/");
      let deadline = new Date(splitDL[2], splitDL[1], splitDL[0]);

      console.log(deadline);
      let diffTime = deadline.getTime() - now.getTime();
      let diffDays = diffTime / (1000 * 3600 * 24);

      return Math.floor(diffDays);
    },
    showCurrentCurrency: function () {
      var formatter = new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
      });
      return formatter.format(this.project.current);
    },
    showMaxCurrency: function () {
      var formatter = new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
      });
      return formatter.format(this.project.max);
    },
  },
};
</script>
<style scoped>
.progress-section {
  margin: 0 auto;
}
.progress .card {
  width: 100%;
}
.section-info {
  padding: 100px;
}
.section-info .col-4:nth-child(2) {
  border-right: 2px solid rgba(0, 0, 0, 0.1);
  border-left: 2px solid rgba(0, 0, 0, 0.1);
}
</style>