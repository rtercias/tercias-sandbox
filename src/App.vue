<template>
  <div id="app">
    <JobRoles />
  </div>
</template>

<script>
import JobRoles from './components/JobRoles.vue'

export default {
  name: 'app',
  components: {
    JobRoles
  }
}
</script>

<style>
body {
  background: #171717;
  color: #fff;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
