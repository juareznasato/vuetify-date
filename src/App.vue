<template>
  <div id="app">
    <VuetifyDate v-model="value" v-bind:label="label" v-bind:config="config" />
    Parent v-model: {{ value }}
  </div>
</template>

<script>
import VuetifyDate from "./components/VuetifyDate.vue";

export default {
  name: "app",
  components: {
    VuetifyDate
  },
  data: () => ({
    value: 1557673468418, // 12/05/2019 12:04:28
    // value:1557630000000, // 12/05/2019
    label: "Data",
    config: {
      locale: "pt-BR",
      format: "DD/MM/YYYY"
    }
  })
};
</script>
