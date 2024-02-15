<template>
    <component :is="routeComponents[currentRoute]"></component>
  </template>
  
  <script>
  import { computed } from 'vue';
  import Home from './Home.vue';
  import About from './About.vue';
  
  export default {
    props: {
      currentRoute: {
        type: String,
        required: true
      }
    },
    components: {
      Home,
      About
    },
    setup(props) {
      const routeComponents = {
        '/': Home,
        '/about': About
      };
  
      return {
        routeComponents
      };
    }
  };
  </script>
  