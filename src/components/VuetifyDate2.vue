<template>
  <div>
    <v-layout row>
      <v-flex xs12 sm6 md4>
        <v-menu
          v-model="menu"
          v-bind:close-on-content-click="false"
          offset-y
          full-width
          max-width="290"
          data-app="true"
        >
          <v-text-field
            slot="activator"
            prepend-icon="event"
            v-model="compShow"
            v-bind:value="compValue"
            v-bind:readonly="readonly"
            v-bind:clearable="options.clearable"
            v-bind:label="label"
          ></v-text-field>
          <v-date-picker v-model="modDate" @change="menu=false, emit()" v-bind:locale="options.locale" no-title></v-date-picker>
        </v-menu>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import moment from "moment";

export default {
  model: { prop: "value", event: "input" },
  props: {
    value: {
      type: [Number, String],
      default: 0
    },
    label: {
      type: String,
      default: "Label"
    },
    options: {
      type: Object,
      default: function() {
        return { locale: "pt-BR", format: "DD/MM/YYYY", clearable: false };
      }
    }
  },
  data: () => ({
    modDate: "",
    modFormattedDate: "",
    time: "00:00:00",
    menu: false,
    readonly: true
  }),
  computed: {
    compValue() {
      const THIS = this;
      return this.value ? THIS.modDate = moment(new Date(this.value)).format("YYYY-MM-DD") : null;
    },
    compShow: {
      get: function () {
        const THIS = this;
        return this.value ? THIS.modFormattedDate = moment(new Date(this.value)).format(this.options.format) : null;
      },
      set: function () {
        const THIS = this;
        THIS.modFormattedDate = null;
        THIS.modDate = null;
        this.$emit("input", null);
      }
    }
  },
  methods: {
    emit() {
      this.$emit("input", this.stringToMillisecond(this.modDate, this.time));
    },
    stringToMillisecond: function(date, time) {
      return Date.parse(date + " " + time);
    }
  }
};
// Str to milli
// var d = Date.parse(date);
// Transformar em data
// milli to date
// this.date = new Date(d);
</script>
