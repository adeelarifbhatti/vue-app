<template>
  <div class="header"> 
    <div class="logo-box">
       <img src="../../public/img/logo2.png" alt="Logo" class="logo">
    </div>
    <div class="logo-box2">
       <img src="../../public/img/logo2.png" alt="Logo" class="logo">
    </div>

  </div>
</template>

<script>
export default {

}
</script>

<style >
.header {
  height: 30vh;
  background-image: linear-gradient(to right bottom, rgba(153, 181, 233, 0.459), rgba(104, 187, 235, 0.404)),
   url(../../public/img/banner.jpg);
  background-size: cover;
  background-size: cover;
  background-position: top;
  position: relative;
  clip-path: polygon(0% 0%, 100% 0, 100% 25vh, 0% 100%); 
}
.logo-box{
    position: absolute;
    top: .9rem;
    left: .1rem; 
  }
.logo-box2 {
    position: absolute;
    top: .9rem;
    right: .1rem; 
  }
.logo {
    height: 8.5rem; 
    }
</style>