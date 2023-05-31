<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="container">
    <header>
      <div class="wrapper">
        <HelloWorld msg="Waikau's Note App" />
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <!-- <RouterLink to="/about">About</RouterLink> -->
        </nav>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<style scoped>
.container {
  max-width: 80vw;
  height: 100%;
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;
}

</style>
