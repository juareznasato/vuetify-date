# vuetify-date

This component works with vuetify. It uses v-text-field and v-date-picker.

v-text-field
- 14/05/2019
- Locale allows you to define other date formats.

v-model parent (input and output in milliseconds)
1557802800000

if you want a datetime component, please, try this:
https://github.com/juareznasato/vuetify-datetime.git

## Features

- Vuetify dependency
- moment dependency
- Works fine with Chrome and Firefox. Others not tested.

## Usage

### Globally:
```
Install:
$ npm install vuetify-date --save

Register component:
import Vue from "vue";
import VuetifyDate from "vuetify-date";
Vue.use(VuetifyDate);
export default VuetifyDate;

Parent component:
<template>
  <div>
    <vuetify-date v-model="value" v-bind:label="label" v-bind:config="config"/>
    v-model parent: {{ value }}
  </div>
</template>
<script>
export default {
  data: () => ({
    value: "1557802800000",
    label: "Date",
    config: {
      locale: "pt-BR",
      format: "DD/MM/YYYY",     - Date format only. Do not include the time format here.
      clearable: true
    }
  })
};
</script>

```
### As component:
```
<template>
  <div>
    <VuetifyDate v-model="value" v-bind:label="label" v-bind:config="config"/>
    v-model parent: {{ value }}
  </div>
</template>
<script>
import VuetifyDate from "@/components/VuetifyDate.vue";
export default {
  components: {
    VuetifyDate
  },
  data: () => ({
    value: "1557802800000",
    label: "Date",
    config: {
      locale: "pt-BR",
      format: "DD/MM/YYYY",     - Date format only. Do not include the time format here.
      clearable: true
    }
  })
};
</script>
```
