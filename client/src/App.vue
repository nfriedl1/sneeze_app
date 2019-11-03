<template>
  <div id="app">
    <Header />
    <SneezeForm v-on:record-sneeze="updateSneezeList" />
    <!-- idea? route to variable data displays: e.g. list, graph by ?, and so on (or both) -->
    <SneezeList v-bind:sneezes="sneezes" />
  </div>
</template>

<script>
import axios from 'axios';
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
      // this.sneezes = [...this.sneezes, sneeze];

      axios.post('https://jsonplaceholder.typicode.com/posts', {userId: 1, id: sneeze.id, title: sneeze.date, body: sneeze.time})
        .then(response => {
          
          this.sneezes = [...this.sneezes, {id: response.data.id, date: response.data.title, time: response.data.body}]
          });
    }
    //deleteSneezeList() TODO using axios.delete() and $emit from SneezeList component
  },
  created() {
    // initialize sneezes from HTTP request
    axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5')
      .then(response => {
        for (let i = 0; i < response.data.length; i++) {
          this.sneezes.push({id: response.data[i].id, date: response.data[i].title.substring(0, 10), time: response.data[i].body.substring(0, 5)})
        }
      });


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
  font-family: MonoSpace, 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
