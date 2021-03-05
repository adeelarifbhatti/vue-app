<template>
  <div class="home">
    <Filter @filterChange="current = $event" :current="current"/>
      <div v-if="projects.length">
          <div v-for="project in filteredProjects" :key="project.id">
            <SingleProject :project="project" @delete="handleDelete" @complete="handleComplete"/>
          </div>
      </div>
  </div>
</template>

<script>
import  SingleProject from '../components/SingleProject.vue'
import  Filter from '../components/Filter.vue'


export default {
  name: 'Home',
  components: {SingleProject,Filter}, 
    data() {
      return {
        projects: [],
        current: 'all'
      }
    },  
  mounted() {
    fetch("http://mol.uio.no:3000/projects")
    .then(res => res.json())
    .then(data => this.projects = data)
    .then(adeel => {console.log("ADEEL TEST LOG",adeel);})
    .catch(err => console.log(err.message))
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id
      });
    },
    handleComplete(id) {
      let p = this.projects.find((project) => {
        return project.id == id
      });
      p.complete = !p.complete
      }
  },
  computed: {
    filteredProjects() {
      if (this.current === 'completed') {
        return this.projects.filter(project => project.complete)
      }
      if (this.current ==='incompleted'){
        return this.projects.filter(project => !project.complete)
      }
      return this.projects
    }
  }  
}
</script>
<style>

</style>