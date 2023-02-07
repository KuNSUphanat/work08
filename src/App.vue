<script setup>
import axios from "axios";
import { ref } from "vue";
const data = ref();

const config = {
  method: "get",
  url: "https://rickandmortyapi.com/api/character/?name=rick&status=alive",
  headers: {},
};
axios(config)
  .then(function (response) {
    data.value = response.data.results;
    console.log(characters.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>


<template>
  <div :style="{backgroundImage:'url(https://upgradingoneself.com/wp-content/uploads/2021/11/rick-and-morty-1024x576.jpg)'}">
  </div>
  <div class="container">
    <h1>The rick and morty Api</h1>
    <table>
      <thead>
        <th><input type = “text” size = “20” name = “name” /></th>
      </thead>
      <tbody>
        <tr v-for="(character, index) in data" :key="index">
          
          <td>{{ character.name }}</td>
          <td>{{ character.status }}</td>
          <td>{{ character.species }}</td>
          <td>{{ character.type }}</td>
          <td>{{ character.gender }}</td>
          <td>{{ character.origin.name }}</td>
          <td>{{ character.location.name }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>