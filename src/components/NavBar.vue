<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-transparent">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"
        ><img :src="require('@/assets/logo.svg')" alt=""
      /></a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link" aria-current="page" href="#">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Discover</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Get Started</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {};
</script>
<style scoped>
.navbar {
  position: absolute;
  top: 0;
  left: 150px;
  width: 80%;
  margin: 0 auto;
  background: transparent !important;
}
nav .navbar-nav li a{
  color: white !important;
  }
</style>