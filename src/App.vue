<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Loader from './components/Loader.vue';
import { reactive } from "vue";



const state = reactive({ isLoading: false });
</script>

<template>
  <div>
    <div v-if="state.isLoading">
      <Loader />
    </div>
    <div v-else>
      <header>
        <div class="wrapper">
          <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
          </nav>
        </div>
      </header>

      <RouterView />
    </div>
  </div>
</template>

<!-- <style scoped lang="SCSS">

</style> -->
