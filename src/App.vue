<template>
  <FileServer1 msg="File Server"/>
</template>

<script>
import FileServer1 from './components/FileServer1.vue'

export default {
  name: 'App',
  components: {
    FileServer1
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
