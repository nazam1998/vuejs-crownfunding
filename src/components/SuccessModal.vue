<template>
  <div
    class="success-modal"
    v-on:clickaway="$root.$emit('change-success-modal')"
  >
    <!-- Modal content -->
    <div class="success-modal-content p-4 text-center w-50">
      <img :src="require('@/assets/icon-check.svg')" alt="" />
      <h4 class="my-4">Thank you for your support</h4>
      <p class="text-muted">
        Your pledge brings us one step closer to sharing Mastercraft Bamboo
        Monitor Riser worldwide. You will get an email once our campaign is
        completed.
      </p>
      <button @click="$root.$emit('change-success-modal')" class="btn-back">
        Got it
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "SuccessModal",
};
</script>
<style>
.success-modal {
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
.success-modal-content {
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