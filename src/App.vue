<template>
  <v-app>
    <v-content> <LoadJSON /> </v-content>
  </v-app>
</template>

<script>
import LoadJSON from "./components/LoadJSON.vue";

export default {
  name: "App",

  components: {
    LoadJSON
  },

  data: () => ({
    //
  })
};
</script>
