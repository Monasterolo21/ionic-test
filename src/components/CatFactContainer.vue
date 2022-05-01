<template>
  <div id="container">
    <strong>{{ title }}</strong>
    <p>
      {{ currentJoke }}
    </p>

    <ion-button color="success" @click="fetchcurrentJoke">
      Get Cat Fact
    </ion-button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButton,
} from "@ionic/vue";

import { IonIcon } from "@ionic/vue";

export default defineComponent({
  name: "currentJokeContainer",
  props: {
    title: String,
  },

  components: {
    IonButton,
  },

  data() {
    return {
      currentJoke: "",
    };
  },

  methods: {
    async fetchcurrentJoke() {
      const response = await fetch("https://currentJoke.ninja/fact");
      const data = await response.json();
      this.currentJoke = data.fact;
    },
  },

  mounted() {
    this.fetchcurrentJoke();
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

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 2em;
}

#container a {
  text-decoration: none;
}
</style>
