<template>
  <div class="app">
    <Navbar />
    <router-view />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Navbar from "./components/Navbar.vue";
import countriesData from "../public/countries.json";

const countries = ref([]);

onMounted(() => {
  countries.value = countriesData;
  console.log('countries.value', countries.value);
})
</script>

<style></style>
