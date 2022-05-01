<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>
          <h1>Jokes</h1>
        </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Jokes</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <p>
          {{ currentJoke.setup }}
        </p>
        <p>
          {{ currentJoke.delivery }}
        </p>
      </div>
    </ion-content>
    <ion-fab vertical="bottom" horizontal="end">
      <ion-fab-button @click="fetchJoke">
        <ion-icon :icon="refreshOutline"></ion-icon>
      </ion-fab-button>
    </ion-fab>
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

import { refreshOutline } from "ionicons/icons";

export default defineComponent({
  name: "Tab1Page",
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
  },

  setup() {
    return {
      refreshOutline,
    };
  },

  data() {
    return {
      currentJoke: "",
    };
  },

  methods: {
    async fetchJoke() {
      const response = await fetch(
        "https://v2.jokeapi.dev/joke/Dark?type=twopart"
      );
      const data = await response.json();
      this.currentJoke = data;
    },
  },

  mounted() {
    this.fetchJoke();
  },
});
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 2em;
  font-size: 1.5em;
}
</style>
