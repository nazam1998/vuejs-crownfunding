<template>
  <div>
    <div
      class="card p-5 my-3"
      @click="selectPledge"
      :class="{ 'border-green': isSelected, 'card-disable': hasNoLeft }"
    >
      <div class="pledge-title row">
        <div class="col-1 mr-2">
          <input
            :checked="isSelected"
            type="radio"
            name="pledge"
            :id="index + 'input-modal'"
          />
        </div>
        <div class="col-10">
          <div class="row">
            <h5 class="card-title col-4">
              {{ hasPledge ? pledge.title : "Pledge with no reward" }}
            </h5>
            <span v-if="hasPledge" class="col-3 span-price"
              >Pledge ${{ pledge.min }} or more</span
            >
            <div v-if="hasPledge" class="col-3 text-muted">
              <span class="pledge-amount">{{ pledge.left }}</span>
              left
            </div>
          </div>
        </div>
      </div>

      <p class="text-muted my-3">
        {{
          hasPledge
            ? pledge.desc
            : "Choose to support us without a reward if you simply believe in our project. As a backer, you will be signed up to receive product updates via email."
        }}
      </p>
      <div class="selected" v-if="isSelected">
        <hr />
        <div class="row justify-content-between">
          <p class="text-muted col-4">Enter Your Pledge</p>
          <div class="col-6 text-end">
            <span class="input w-50 mx-2"
              >&#36;<input
                name="budget"
                type="number"
                v-model="userChoice"
                data-errormessage-value-missing="Uh oh, somethings wrong!"
                data-errormessage-type-mismatch="Uh oh, somethings wrong!"
            /></span>
            <button class="btn-back" @click="addFunds">Continue</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Pledge",
  data() {
    return {
      userChoice: 0,
    };
  },
  props: {
    pledge: [Object, String],
    index: Number,
    project: Object,
    current: [Number, String],
  },
  mounted() {
    this.userChoice = this.hasPledge ? this.pledge.min : 0;
  },
  methods: {
    selectPledge: function () {
      let value = this.hasPledge ? this.index : "None";
      this.$emit("selectPledge", value);
    },
    addFunds: function () {
      this.$root.$emit("addFunds", [this.pledge, this.userChoice, this.index]);
    },
  },
  watch: {
    userChoice: function (value) {
      let diff = this.project.max - this.project.current;
      let min = this.hasPledge ? this.pledge.min : 1;
      if (value < min) {
        this.userChoice = diff;
      }
    },
  },
  computed: {
    checkStock: {
      get: function () {
        return this.hasPledge && this.hasNoLeft
          ? "Out of Stock"
          : "Select Reward";
      },
    },
    hasNoLeft: function () {
      return this.pledge.left <= 0;
    },
    hasPledge: {
      get: function () {
        return this.pledge != "None";
      },
    },
    isSelected: {
      get: function () {
        return (
          (this.current == "None" && !this.hasPledge) ||
          this.index == this.current
        );
      },
    },
  },
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

.border-green {
  border-color: #3cb4ab;
}
.input {
  border-radius: 40px;
  padding: 10px 20px;
  border: 1px inset #ccc;
}
input[type="number"] {
  border: none;
}
.card {
  cursor: pointer;
}
.card:hover h5.card-title {
  color: #3cb4ab;
}
.card-disable {
  opacity: 0.2;
  cursor: not-allowed;
  color: black;
}
.card-disable:hover h5.card-title {
  color: black;
}
</style>