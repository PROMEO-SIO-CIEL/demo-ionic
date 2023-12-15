<template>
  <div class="city__item">
    <h2>{{ props.city.nom }}</h2>
    <p>Population: {{ props.city.population }}</p>
  </div>
</template>

<script setup>
const props = defineProps(['city']);
</script>