<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-input label="Code postal" v-model="postalCode" placeholder="60200" />
      <ion-button @click="handleClick" expand="full">Rechercher</ion-button>
      <div v-if="postalCode !== '' && cityArray.length > 0">
        <h1>Ville(s) pour {{ postalCode }} :</h1>
        <CityList :cities="cityArray"/>
      </div>
      <div v-else>
        <p>Aucun résultat !</p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton, IonInput } from '@ionic/vue';
import {ref} from "vue";
import CityList from "../components/CityList.vue";

const postalCode = ref("");
const cityArray = ref([]);

const handleClick = async () => {
  cityArray.value = [];
  const response = await fetch('https://geo.api.gouv.fr/communes?codePostal=' + postalCode.value);
  const data = await response.json();
  cityArray.value = data;
}
</script>

<style scoped>

</style>
