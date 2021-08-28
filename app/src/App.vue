<template>
  <div id="app">
    <h1>periodic table</h1>
    <Table :elements="elementsData"/>
  </div>
</template>

<script>
import Table from './components/Table.vue';
import TableData from './data/periodic-table-data.json';

export default {
    data() {
    return {
      elementsData: TableData
    }
  },
  name: 'App',
  components: {
    Table,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
};

body {
  background:#F2ECE9;
  font-family: 'Montserrat';
  display: flex;
  justify-content: center;
  box-sizing: border-box;
  margin: 0 auto;
}

h1 {
  text-transform: uppercase;
  font-size: 1rem;
  letter-spacing: 2px;
}
</style>
