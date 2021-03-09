<template>
  <Header />
  <Navigation />
  <router-view/>
  <Footer />
</template>


<script>
import Navigation from './components/Navigation.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
export default {
  components: { Navigation, Header, Footer }
  

}
</script>
<style lang="scss">
@import './assets/scss/scss.scss' 

</style>
