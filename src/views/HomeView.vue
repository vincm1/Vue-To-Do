<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :project="project" @complete="handleComplete" @delete="handleDelete"/>
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject.vue'

export default {
  name: 'HomeView',
  components: {SingleProject},
  data () {
    return {
      projects: [],
    } 
  },
  mounted() {
    fetch('http://localhost:3000/projects')
      .then(response => response.json())
      .then(data => this.projects = data)
      .catch(err => console.log(err.message))
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id})
    },
    handleComplete(id) {
      let proj = this.projects.find((project) => {
        return project.id === id})
      proj.complete = !proj.complete
      }
    }
  }

</script>

<style>
</style>