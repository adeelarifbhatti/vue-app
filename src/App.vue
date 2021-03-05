<template>
  <Header />
  <Navigation class="slim" />
  <router-view/>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Header from './components/Header.vue'
export default {
  components: { Navigation, Header }
  

}
</script>
<style>
body {
  background: linear-gradient(to right bottom, rgba(122, 124, 128, 0.658), rgba(104, 187, 235, 0.603));
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: auto;
  margin: 0 auto;
  color: rgb(85, 100, 102);
}
.slim {
  max-width: 90%;
}
</style>
