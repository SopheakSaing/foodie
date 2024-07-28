<template>
  <div class="flex p-8 flex-col items-center justify-center">
    <input
      type="text"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for Meal"
    />
    <div class="flex gap-1">
      <!-- <pre>{{letters}}</pre> -->
      <router-link to="/" v-for="letter of letters" :key="letter">
        {{ letter }}
      </router-link>
    </div>
  </div>
</template>


<script setup>
import { computed } from "vue";
import store from "../store";

const meals = computed(() => store.state.meals); //return meal
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
</script>


//composition api - use setup attribute