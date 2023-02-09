<script setup>
import axios from "axios";
import { ref } from "vue";

const data = ref();
const config = {
  method: "get",
  url: "https://swapi.dev/api/people",
  headers: {},
};

axios(config)
  .then(function (response) {
    data.value = response.data.results;
    console.log(data.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>
<template>
  <div class="container">
    <h1>The Starwars Api</h1>
    <table>
      <thead style="background: gray">
        <th>Name</th>
        <th>Hair Color</th>
        <th>Eyes Color</th>
        <th>Skin Color</th>
      </thead>
      <tbody>
        <tr v-for="(value, index) in data" :key="index">
          <td>{{ value.name }}</td>
          <td>{{ value.hair_color }}</td>
          <td>{{ value.eye_color }}</td>
          <td>{{ value.skin_color }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
