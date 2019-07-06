# vuetify-date

This component works with vuetify.

input:
- 14/05/2019   (Locale allows you to define others date formats).

v-model: (milliseconds)
1557802800000

if you want a datetime component, please, try this:
<p><a href="https://github.com/juareznasato/vuetify-datetime.git" target="_blank">vuetify-datetime</a></p>

## Dependency
- VueJS
- Vuetify
- moment

## Links
<p><a href="https://46zdr.codesandbox.io/" target="_blank">See DEMO here</a></p>
<p><a href="https://github.com/juareznasato/vuetify-date" target="_blank">GitHub</a></p>
<p><a href="https://www.npmjs.com/package/vuetify-date" target="_blank">npm</a></p>

## Install:
```
$ npm install vuetify-date --save

Register component:

1- Create a src/modules/vuetify-date.js file with the following content:
import Vue from "vue";
import VuetifyDate from "vuetify-date";
Vue.use(VuetifyDate);
export default VuetifyDate;

2- Add to src/mains.js file:
import "./modules/vuetify-date.js";

Parent component:
<template>
  <div>
    <vuetify-date v-model="value" v-bind:label="label" v-bind:options="options"/>
    v-model parent: {{ value }}
  </div>
</template>
<script>
export default {
  data: () => ({
    value: "1557802800000",
    label: "Date",
    options: {
      locale: "pt-BR",
      format: "DD/MM/YYYY",     - Date format only. Do not include the time format here.
      clearable: true
    }
  })
};
</script>

