<template>
  <div id="app">
    <Header />
    <SneezeForm v-on:record-sneeze="updateSneezeList" />
    <!-- idea? route to variable data displays: e.g. list, graph by ?, and so on (or both) -->
    <SneezeList v-bind:sneezes="sneezes" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import SneezeForm from './components/SneezeForm.vue';
import SneezeList from './components/SneezeList.vue';

export default {
  name: 'app',
  components: {
    Header,
    SneezeForm,
    SneezeList
  },
  data() {
    return {sneezes: []}
  },
  methods: {
    updateSneezeList(sneeze) {
      this.sneezes = [...this.sneezes, sneeze];
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
