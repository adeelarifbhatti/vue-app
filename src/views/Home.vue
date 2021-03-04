<template>
  <div class="home">
      <div v-if="projects.length">
          <div v-for="project in projects" :key="project.id">
            <p> {{ project.title }} </p>
          </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {},
    data() {
      return {
        projects: []
      }
    },  
  mounted() {
    fetch("http://mol.uio.no:3000/project")
    .then(res => res.json())
    .then(data => this.projects = data)
    .then(adeel => {console.log("ADEEL TEST LOG",adeel);})
    .catch(err => console.log(err.message))
  }
}
</script>
