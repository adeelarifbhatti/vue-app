<template>
  <Navigation/>
  <router-view/>
</template>

<script>
import Navigation from './components/Navigation.vue'
export default {
  components: { Navigation }
  

}
</script>
<style>
body {
  background: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #565;
}


</style>
