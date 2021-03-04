<template>
  <div class="home">
      <div v-if="projects.length">
          <div v-for="project in projects" :key="project.id">
            <SingleProject :project="project"/>
          </div>
      </div>
  </div>
</template>

<script>
import  SingleProject from '../components/SingleProject.vue'

export default {
  name: 'Home',
  components: {SingleProject},
    data() {
      return {
        projects: []
      }
    },  
  mounted() {
    fetch("http://mol.uio.no:3000/projects")
    .then(res => res.json())
    .then(data => this.projects = data)
    .then(adeel => {console.log("ADEEL TEST LOG",adeel);})
    .catch(err => console.log(err.message))
  }
}
</script>