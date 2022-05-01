<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Fact Container</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Cat Fact</ion-title>
        </ion-toolbar>
      </ion-header>

      <CatFactContainer />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";
import CatFactContainer from "@/components/CatFactContainer.vue";

export default defineComponent({
  name: "Tab1Page",
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    CatFactContainer,
  },
});
</script>
