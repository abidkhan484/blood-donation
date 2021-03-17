<template>
  <div class="container">
      <DonorList />
  </div>
</template>

<script>
import DonorList from './components/DonorList.vue'

export default {
  name: 'App',
  components: {
    DonorList
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
