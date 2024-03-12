<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Goats from './components/Goats.vue';
import { NMessageProvider } from "naive-ui";
import Navbar from './components/Navbar.vue';

</script>

<template>
  <n-message-provider>
    <Navbar />
    <main>
      <div class="wrapper">

      </div>
      <RouterView />
    </main>
  </n-message-provider>
</template>

<style scoped></style>
