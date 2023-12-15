<template>
  <div class="city__list">
    <CityItem v-for="(city, index) in props.cities" :key="index" :city="city"/>
  </div>
</template>

<script setup>
import CityItem from "./CityItem.vue";

const props = defineProps(['cities']);
</script>
