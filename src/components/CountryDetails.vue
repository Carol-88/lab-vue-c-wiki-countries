<template>
  <div class="country-details" v-if="country">
    <img
      :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`"
      alt="Flag"
    />
    <h1>{{ country.name.common }}</h1>
    <table class="table">
      <tbody>
        <tr>
          <td style="width: 30%">Capital</td>
          <td>{{ country.capital[0] }}</td>
        </tr>
        <tr>
          <td>Area</td>
          <td>{{ country.area }} km<sup>2</sup></td>
        </tr>
        <tr>
          <td>Borders</td>
          <td>
            <ul>
              <li v-for="border in country.borders" :key="border">
                <a :href="`/${border.toUpperCase()}`">{{ border }}</a>
              </li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";
import countriesData from "/public/countries.json";

const country = ref(null);
const route = useRoute();

onMounted(() => {
  const alpha3Code = route.params.alpha3Code;
  const foundCountry = countriesData.find((c) => c.alpha3Code === alpha3Code);
  if (foundCountry) {
    country.value = foundCountry;
  } else {
    console.error(`País con código alfa-3 ${alpha3Code} no encontrado.`);
  }
});
</script>
