<template>
  <div class="progress-section">
    <div class="card w-75 mx-auto my-4">
      <div class="section-info">
        <div class="row justify-content-between">
          <div class="col-4">
            <h1>$89,914</h1>
            <p class="text-muted">of $100.000 backed</p>
          </div>
          <div class="col-4">
            <h1>5,007</h1>
            <p class="text-muted">total backers</p>
          </div>
          <div class="col-4">
            <h1>56</h1>
            <p class="text-muted">days left</p>
          </div>
        </div>
        <div class="progress mt-5 border-rounded">
          <div
            class="progress-bar"
            role="progressbar"
            style="width: 25%; border-radius: 10px; background-color: #3bb4ad;"
            aria-valuenow="25"
            aria-valuemin="0"
            aria-valuemax="100"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {};
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