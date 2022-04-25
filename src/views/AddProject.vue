<template>
  Add Project
  <form @submit.prevent="handleSubmit">
      <label >Title:</label>
      <input type="text" v-model="title">
      <label >Details:</label>
      <input type="text" v-model="details">
      <button>Add Project</button>
  </form>
</template>

<script>
export default {
data(){
    return{
        title: '',
        details: ''

    }
},
methods: {
    handleSubmit(){
        let project = {
            title: this.title,
            details: this.details,
            complete: false

        }
        fetch('http://localhost:3000/projects', {
            method: 'POST',
            headers: {'Content-type': 'application/json'},
            body: JSON.stringify(project)
        }).then(() =>this.$router.push('/')
        ).catch(err => console.log(err.message))
    }
}
}
</script>

<style>

</style>