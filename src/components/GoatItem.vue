<template>
    <div class="goat-item">
      <img :src="goat.image" alt="Goat" />
      <h2>{{ goat.name }}</h2>
      <p>{{ goat.description }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      goat: Object, // Assuming you pass a goat object as a prop
    },
  };
  </script>
  
  <style scoped>
  /* Add your component-specific styles here */
  .goat-item img {
    max-height: 20vh;
  }
  </style>
  