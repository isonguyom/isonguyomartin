<script setup>
import { RouterView } from 'vue-router'
import { reactive } from "vue";
import Loader from './components/Loader.vue';
import Nav from './components/Nav.vue';



const state = reactive({ isLoading: false });
</script>

<template>
  <div>
    <div v-if="state.isLoading">
      <Loader />
    </div>
    <div v-else>
      <Nav />
      <RouterView />
    </div>
  </div>
</template>

<!-- <style scoped lang="SCSS">

</style> -->
