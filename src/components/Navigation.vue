<template>
  <nav class="navigation">
      <router-link class="navigation-tabs" :to="{name: 'Home'}">
          Projects
      </router-link>
      <router-link class="navigation-tabs" :to="{name: 'AddProject'}">
          Add Project
      </router-link>
  </nav>
</template>

<script>
export default {

}
</script>
<style>
.navigation-tabs{
    margin: 3rem;
    padding-top: 3rem;
    margin: 1rem 1rem;
    font-size: 1.4rem;
    text-decoration: none;
    color: black;

}
.navigation{
    margin: 3rem auto;
    padding: 1rem 2rem;
    border-radius: 8%;
    background: rgba(192, 174, 174, 0.288);
    border-style: double;
}



</style>