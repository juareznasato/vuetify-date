# vuetify-date

This component works with v-text-field (vuetify).

v-text-field
14/05/2019 or others formats.

v-model parent (millisecond)
1557802800000

## Features

- Vuetify Dependency
- Works fine with Chrome and Firefox. Others not tested.

## Usage:

### Globally
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
    <VuetifyDate v-model="value" v-bind:label="label" v-bind:config="config"/>
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
      format: "DD/MM/YYYY",
      clearable: true
    }
  })
};
</script>

```
### As component
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
      format: "DD/MM/YYYY",
      clearable: true
    }
  })
};
</script>
```
