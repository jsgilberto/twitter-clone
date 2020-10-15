<template>
<div id="app">
  <div class="container">
    <UserProfile/>
  </div>
  
</div>
</template>

<script>
import UserProfile from './components/UserProfile.vue'

export default {
  name: 'App',
  components: { UserProfile }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding-top: 40px;
  padding-bottom: 40px;
  min-height: 100vh;
  background-color: #f1f1f1;
}
</style>
