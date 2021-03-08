<template>
  <div class="home">
    <Filter @filterChange="current = $event" :current="current"/>
      <div v-if="projects.length">
          <div v-for="project in filteredProjects" :key="project.id">
            <SingleProject :project="project" @delete="handleDelete" @complete="handleComplete"/>
          </div>
      </div>
  </div>
    <Footer />
</template>

<script>
import  SingleProject from '../components/SingleProject.vue'
import  Filter from '../components/Filter.vue'
import Footer from '../components/Footer.vue'


export default {
  name: 'Home',
  components: {SingleProject,Filter,Footer}, 
    data() {
      return {
        projects: [],
        current: 'all'
      }
    },  
  mounted() {
    console.log("ADEEL JEE",process.env.VUE_APP_URL);
    fetch(process.env.VUE_APP_URL)
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