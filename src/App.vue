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
<style lang="scss">
@import './assets/scss/scss.scss' 

</style>
