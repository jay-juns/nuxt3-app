<template>
<div>
  <form action="forms" @submit.prevent="searchForStuff">
    <input type="text" v-model="searchText" />
    <button type="submit">TV 검색</button>
  </form>
  <div class="stuff">
    <div v-for="show in myData" :key="show.id">
      <img :src="show.show?.image?.medium" alt="img" />
    </div>
  </div>
</div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const searchText = ref("")
const myData = ref([]) as any;

async function searchForStuff() {
  const data = await fetch(`/api/hello?search=${searchText.value}`);
  const json = await data.json();
  console.log('json', json);
  myData.value = json;
}

</script>

<style>

</style>