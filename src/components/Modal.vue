<template>
  <div class="pledge-modal" v-on:clickaway="$root.$emit('change-modal')">
    <!-- Modal content -->
    <div class="pledge-modal-content p-5">
      <span class="close" @click="$root.$emit('change-modal')">&times;</span>
      <h4>Back this Project</h4>

      <p class="text-muted">
        Want to support us in bringing Mastercraft Bamboo Monitor Riser out in
        the world?
      </p>
      <PledgeModal :current="current" :project="project" :pledge="'None'" @selectPledge="selectPledge"/>
      <PledgeModal v-for="(pledge, index) in project.pledges" :index="index" :current="current" :project="project" @selectPledge="selectPledge" :key="index" :pledge="pledge"/>
    </div>
  </div>
</template>
<script>
import PledgeModal from "@/components/PledgeModal";

export default {
  name: "Modal",
  components: {
    PledgeModal
  },
  props: {
    project: Object
  },
  data(){
    return{
      current: null
    }
  },
  methods: {
    selectPledge: function(value){
      this.current = value;
      console.log(this.current);
    }
  }
};
</script>
<style scoped>
.pledge-modal {
  position: fixed; /* Stay in place */
  z-index: 20; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */
}

/* Modal Content/Box */
.pledge-modal-content {
  background-color: #fefefe;
  margin: 15% auto; /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 80%; /* Could be more or less, depending on screen size */
}

/* The Close Button */
.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>