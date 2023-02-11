<script setup>
import { ref } from "vue";
import axios from "axios";

const data = ref([]);
const config = {
  method: "get",
  url: "https://date.nager.at/api/v3/PublicHolidays/2023/AT",
  headers: {},
};
axios(config)
  .then(function (response) {
    data.value = response.data;
    console.log(response.data);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>

<template>
  <h3>Public Holidays</h3>
  <table>
    <tr>
      <th></th>
    </tr>
    <tr v-for="product in data" :key="product.data">
      <td>{{ product.date }}</td>
      <td>{{ product.localName }}</td>
      <td>{{ product.name }}</td>
      <td>{{ product.countryCode }}</td>
    </tr>
  </table>
</template>

<style scoped></style>