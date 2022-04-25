<template>
  <nav class="main-nav">
      <router-link :to="{name:'Home'}">Projects</router-link>
      <router-link :to="{name:'AddProject'}">Add Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style scoped>
.main-nav{
    margin: 30px 0;

}
.main-nav a{
  margin:  10px;
  text-decoration: none;
  padding-bottom: 5px;
}
a.router-link-active{
  border-bottom: 4px solid aquamarine;
}

</style>