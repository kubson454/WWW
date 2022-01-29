<template>
  <div>
    <h1>Witam</h1>
    <p>Witamy na stronie opisującej bibliotekę Vue.JS</p>
    <div v-if="activity">
      <p>Dzisiejsze losowe zadanie to: {{ activity }}</p>
    </div>
    <div v-else>Proszę poczekać, API jest w trakcie ładowania</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      activity: "",
    };
  },

  // Fetches posts when the component is created.
  created() {
    axios
      .get(`https://www.boredapi.com/api/activity`)
      .then((response) => {
        // JSON responses are automatically parsed.
        this.activity = response.data.activity;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
