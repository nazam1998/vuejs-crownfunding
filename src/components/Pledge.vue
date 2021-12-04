<template>
  <div class="pledge">
    <div
      class="card p-5 my-3 border-secondary"
      :class="{ 'card-disable': hasNoLeft }"
    >
      <div class="pledge-title row justify-content-between">
        <h5 class="card-title col-3">{{ pledge.title }}</h5>
        <span class="col-3 span-price">Pledge ${{ pledge.min }} or more</span>
      </div>
      <p class="text-muted my-3">{{ pledge.desc }}</p>
      <div class="row justify-content-between">
        <div class="col-3 text-muted">
          <span class="pledge-amount">{{ pledge.left }}</span> left
        </div>
        <div class="col-5 text-end">
          <button
            @click="showModal"
            :class="{
              'btn-select': !hasNoLeft,
              'btn-disable': hasNoLeft,
            }"
            :disabled="hasNoLeft"
          >
            {{ checkStock }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Pledge",
  props: {
    pledge: Object,
  },
  computed: {
    checkStock: function () {
      return this.hasNoLeft ? "Out of Stock" : "Select Reward";
    },
    hasNoLeft: function () {
      return this.pledge.left <= 0;
    },
  },
  methods: {
    showModal: function (){
      this.$root.$emit("change-modal")
    }
  }
};
</script>
<style scoped>
.card-title {
  font-weight: 1000;
}
.span-price {
  color: #3cb4ab;
  font-weight: bold;
}
.pledge-amount {
  font-weight: bold;
  font-size: 26px;
  color: #000;
}
.btn-select {
  border-radius: 40px;
  padding: 10px 40px;
  background-color: #3cb4ab;
  color: white;
  border: none;
}
.btn-disable {
  border-radius: 40px;
  padding: 10px 40px;
  background-color: black;
  color: white;
  border: none;
}
.card-disable {
  opacity: 0.2;
}
</style>