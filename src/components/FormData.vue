<template>
  <v-form ref="form">
    <v-container fluid>
      <v-row align="center">
        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="name"
            :rules="genericRules"
            label="Nombre"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="lastname"
            :rules="genericRules"
            label="Apellido Paterno"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="surname"
            :rules="genericRules"
            label="Apellido Materno"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="curp"
            :counter="18"
            :rules="curpRules"
            label="CURP"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="rfc"
            :counter="13"
            :rules="rfcRules"
            label="RFC"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="zipcode"
            :counter="5"
            :rules="numberRules"
            label="Codigo Postal"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="street"
            :counter="5"
            :rules="streetRules"
            label="Calle"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="number"
            :counter="5"
            :rules="numberRules"
            label="Numero exterior"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="suite"
            :counter="10"
            :rules="suiteRules"
            label="Numero interior"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            v-model="state"
            :rules="genericRules"
            label="Estado"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            class="mr-10"
            v-model="city"
            :rules="genericRules"
            label="Delegacion/Municipio"
            required
          ></v-text-field>
        </v-col>

        <v-col class="d-flex" cols="12" sm="6">
          <v-text-field
            class="mr-10"
            v-model="colony"
            :rules="genericRules"
            label="Colonia"
            required
          ></v-text-field>
        </v-col>

        <v-btn color="success" class="mr-4" @click="validate">Guardar</v-btn>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data: () => ({
    name: "",
    lastname: "",
    surname: "",
    curp: "",
    curpRules: [
      (v) => !!v || "Existen campos por validar",
      (value) => {
        if (/^[A-Z\d]{18}$/.test(value)) return true;
        return "no coincide con el formato adecuado";
      },
    ],
    rfc: "",
    rfcRules: [
      (v) => !!v || "Existen campos por validar",
      (value) => {
        if (/^[A-ZÑ&]{3,4}\d{6}(?:[A-Z\d]{3})?$/.test(value)) return true;
        return "no coincide con el formato adecuado";
      },
    ],
    street: "",
    streetRules: [(v) => !!v || "Existen campos por validar"],
    zipcode: "",
    number: "",
    numberRules: [
      (v) => !!v || "Existen campos por validar",
      (v) => (v && v.length <= 5) || "Debe ser minimo 5 caracteres",
      (value) => {
        if (/^([0-9])*$/.test(value)) return true;
        return "solo se permiten numeros";
      },
    ],
    suite: "",
    suiteRules: [
      (v) => !!v || "Existen campos por validar",
      (v) => (v && v.length <= 10) || "Debe ser menor a 10 caracteres",
    ],
    state: "",
    city: "",
    colony: "",
    genericRules: [
      (v) => !!v || "Existen campos por validar",
      (value) => {
        if (/[^0-9]/.test(value)) return true;
        return "Solo se permiten Letras";
      },
    ],
    dialog: false,
  }),
  methods: {
    validate() {
      this.$refs.form.validate();
    },
  },
};
</script>
