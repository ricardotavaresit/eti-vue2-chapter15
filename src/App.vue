<template>
  <div id="app">
    <h1>{{ msg }}</h1>
    <search-component />
  </div>
</template>

<script>
import SearchComponent from './components/SearchComponent';
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Chapter 15",
    };
  },
  components:{
    SearchComponent
  }
};
</script>