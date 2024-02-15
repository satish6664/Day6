<template>
  <div>
    <div class="cls">
    <button @click="navigate('/')">Home</button> &nbsp;
    <button @click="navigate('/about')">About</button>
  </div>
    <router-view :current-route="currentRoute"></router-view>
  </div>
</template>

<script>
import { ref } from 'vue';
import RouterView from './components/RouterView.vue';

export default {
  components: {
    RouterView
  },
  setup() {
    const currentRoute = ref(window.location.pathname);

    const navigate = (path) => {
      currentRoute.value = path;
      window.history.pushState(null, '', path);
    };

    window.addEventListener('popstate', () => {
      currentRoute.value = window.location.pathname;
    });

    return {
      currentRoute,
      navigate
    };
  }
};
</script>
<style>

.cls
{
  padding: 8px 90px;
  display: flex;
  justify-content: space-evenly;
}
</style>
