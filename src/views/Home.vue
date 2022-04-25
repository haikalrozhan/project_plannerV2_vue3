<template>
  <FilterNav @filter="current = $event" :current="current"/>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id">
        <SingleProject :project="project" @delete="handleDelete" @complete="handleComplete"/>
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject.vue'
import FilterNav from '../components/FilterNav.vue'

export default {

  name: 'Home',
  components: {
   SingleProject, FilterNav
  },
  data(){
    return{
      projects: [],
      current: 'all'
    }
  },
  methods: {
    handleDelete(id){
      this.projects = this.projects.filter(project => project.id !== id)
    },
    handleComplete(id){
      let p = this.projects.find(project => project.id === id)
      p.complete = !p.complete
    }
  },
  mounted(){
    fetch('http://localhost:3000/projects')
    .then(res => res.json())
    .then(data => this.projects = data)
    .catch(err => console.log(err.message))
  },
  computed: {
    filteredProjects(){
      if(this.current === 'ongoing'){
      return this.projects.filter(project => !project.complete)
      }
      if(this.current === 'complete'){
      return this.projects.filter(project => project.complete)
      }
      return this.projects
      

    }
   
  }
}
</script>
