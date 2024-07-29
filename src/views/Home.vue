<template>
  <div class="flex p-8 flex-col">
    <input
      type="text"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for Meal"
    />
    <div class="flex gap-1 items-center justify-center mt-2">
      <!-- <pre>{{letters}}</pre> -->
      <router-link
        :to="{ name: 'byLetter', params: { letter } }"
        v-for="letter of letters"
        :key="letter"
      >
        {{ letter }}
      </router-link>
    </div>
    <pre>{{ ingredients }}</pre>
  </div>
</template>


<script setup>
import {ref, computed, onMounted } from "vue";
import store from "../store";
import axiosClient from "../axiosClient.js";

const meals = computed(() => store.state.meals); //return meal
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const ingredients = ref([])

onMounted(async () => {
  const response = await axiosClient.get("/list.php?c=list");
  console.log(response.data);
  ingredients.value = response.data;

});
</script>


//composition api - use setup attribute