<template>
  <nav class="navigation">
      <router-link :to="{name: 'Home'}">
          <button class="btn btn__nav">Projects </button>
      </router-link>
      <router-link :to="{name: 'AddProject'}">
          <button class="btn btn__nav"> Add Project</button>
      </router-link>
  </nav>
</template>

<script>
export default {

}
</script>
<style>

</style>