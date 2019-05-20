<template>
  <v-app id="inspire">
    <v-toolbar dark app fixed clipped-left color="cyan"></v-toolbar>
    <v-content>
      <VuetifyDate v-model="value" v-bind:label="label" v-bind:options="options" />
      Parent v-model: {{ value }}
    </v-content>
  </v-app>
</template>

<script>
import VuetifyDate from "./components/VuetifyDate.vue";

export default {
  name: "app",
  components: {
    VuetifyDate
  },
  data: () => ({
    value: 1577239200000, //1557673468418, // 12/05/2019 12:04:28
    label: "Data",
    options: {
      locale: "pt-BR",
      format: "DD/MM/YYYY",
      clearable: true
    }
  })
};
</script>
