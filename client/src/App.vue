<template>
  <div id="app">
    <Header />
    <SneezeForm v-on:record-sneeze="updateSneezeList" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import SneezeForm from './components/SneezeForm.vue';

export default {
  name: 'app',
  components: {
    Header,
    SneezeForm
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
