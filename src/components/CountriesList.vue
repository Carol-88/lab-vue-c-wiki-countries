<template>
  <div class="countries-list">
    <ul>
      <li v-for="country in countries" :key="country.alpha3Code">
        <router-link :to="`/${country.alpha3Code}`">
        {{ country.name.common }}
      </router-link>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue";
import countriesData from "/public/countries.json";

const countries = ref(countriesData);
</script>
