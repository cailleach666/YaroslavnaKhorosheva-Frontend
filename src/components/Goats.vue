<template>
    <div id="goats">
      <GoatItem v-for="goat in goats" :key="goat.id" :goat="goat" />
    </div>
  </template>
  
  <script>
  import Axios from "axios";
  import GoatItem from "./GoatItem.vue";
  
  export default {
    components: {
      GoatItem,
    },
    data() {
      return {
        goats: [],
      };
    },
    created() {
      // Make a GET request using Axios to fetch goat data
      Axios.get("http://localhost:8080/kitsed")
        .then((response) => {
          this.goats = response.data;
        })
        .catch((error) => {
          console.error("Error fetching goat data:", error);
        });
    },
  };
  </script>
  
  <style>
  /* Add your global styles here */
  #goats {
    display: flex;
    flex-wrap: wrap;
    justify-content:flex-start;
    gap: 2rem;
  }
  </style>
  