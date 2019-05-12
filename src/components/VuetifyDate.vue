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
        >
          <v-text-field
            slot="activator"
            prepend-icon="event"
            v-model="modValue"
            v-bind:readonly="readonly"
            v-bind:clearable="clearable"
            v-bind:value="compValue"
            v-bind:label="label"
          ></v-text-field>
          <v-date-picker v-model="date" @change="menu=false, emit()" v-bind:locale="locale" no-title></v-date-picker>
        </v-menu>
      </v-flex>
    </v-layout>
    Child v-model: {{ modValue }}<br>
    Child value: {{ value }}
  </div>
</template>

<script>
import moment from "moment";

export default {
  model: { prop: "value", event: "input" },
  props: {
    value: {
      type: Number,
      default: 0
    },
    label: {
      type: String,
      default: "Label"
    },
    config: {
      type: Object,
      default: function() {
        return { locale: "pt-BR", format: "DD/MM/YYYY" };
      }
    }
  },
  data: () => ({
    modValue: "",
    time: "00:00:00",
    menu: false,
    readonly: true,
    clearable: false,
    locale: "pt-BR",
  }),
  computed: {
    compValue() {
      const THIS = this;
      // return this.value ? THIS.modValue = moment(new Date(this.value)).format(this.config.format) : "";
      return this.value ? THIS.modValue = THIS.humanFormat(this.value) : "";
    }
  },
  methods: {
    emit() {
      this.$emit("input", this.machineFormat(this.modValue + " " + this.time));
    },
    /* Formatar no padrão millisegundo */
    machineFormat: function(date) {
      return date ? Date.parse(this.getDate()) : null;
    },
    /* Formatar no padrão data */
    humanFormat: function(millisecond) {
      return millisecond ? moment(new Date(millisecond)).format(this.config.format) : "";
    },
    /* Data do tipo Date() */
    getDate: function() {
      return this.date !== null ? new Date(this.date + " " + this.time) : null;
    },
    /* Data do tipo Date() */
    setDate(date) {
      this.date = moment(date).format("YYYY-MM-DD");
    },
    /* Milisegundos */
    getMillisecond: function() {
      return this.date !== null ? Date.parse(this.getDate()) : null;
    },
    /* Milisegundos */
    setMillisecond: function(millisecond) {
      this.setDate(new Date(millisecond));
    },
    /* String "YYYY-MM-DD HH:mm:ss" */
    getStringDate: function() {
      return this.date != null
        ? moment(this.date + " " + this.time).format("YYYY-MM-DD HH:mm:ss")
        : null;
    },
    /* String "YYYY-MM-DD HH:mm:ss" */
    setStringDate(date) {
      this.date = date;
    },
    setLabel(label) {
      this.label = label;
    },
    setLocale(locale) {
      this.locale = locale;
    },
    setFormat(format) {
      this.format = format;
    },
    setReadonly(readonly) {
      this.readonly = readonly;
    },
    /* Habilita opção para limpeza do v-textfield */
    setClearable(clearable) {
      this.clearable = clearable;
    },
    clear() {
      this.date = null;
    }
  }
};
// format: "DD/MM/YYYY HH:mm:ss", entrada "2019-02-22 13:54:12"
// setStringDate(date) {
//   // this.date = moment(date).toDate();
//   // ou
//   // Transformar em milissegundos
//   // var d = Date.parse(date);
//   // Transformar em data
//   // this.date = new Date(d);
// },
</script>


