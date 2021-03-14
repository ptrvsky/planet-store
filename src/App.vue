<template>
  <div id="app">
    <Header/>
    <index/>
  </div>
</template>

<script>
import Index from './components/Index.vue'
import Header from "@/components/Header";

export default {
  name: 'App',
  components: {
    Header,
    Index
  }
}
</script>

<style>
@import 'styles/main.scss';
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap');

body {
  margin: 0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
