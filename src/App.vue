<template>
  <Navbar/>
  <router-view/>
</template>
<script>
import Navbar from './components/Navbar.vue'
export default{
components: {Navbar}
}
</script>
<style>
body{
  background: #f5f5f5;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 40px auto;

}
</style>
