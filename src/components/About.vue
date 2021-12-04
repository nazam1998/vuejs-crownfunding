<template>
  <div class="about">
    <div class="card mx-auto p-5 w-75">
      <div class="section-about">
        <h2 class="mt-3">About this project</h2>

        <p class="mt-5 text-muted">
          The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform
          that elevates your screen to a more comfortable viewing height.
          Placing your monitor at eye level has the potential to improve your
          posture and make you more comfortable while at work, helping you stay
          focused on the task at hand.
        </p>
        <p class="mt-5 text-muted">
          Featuring artisan craftsmanship, the simplicity of design creates
          extra desk space below your computer to allow notepads, pens, and USB
          sticks to be stored under the stand.
        </p>
      </div>
      <Pledge/>
    </div>
  </div>
</template>
<script>
import Pledge from "@/components/Pledge";
export default {
  name: "About",
  components: {
    Pledge
  }
};
</script>
<style scoped>
.section-about h2 {
  font-weight: 1000;
}
</style>