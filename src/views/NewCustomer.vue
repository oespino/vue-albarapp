<template>
  <v-content>
    <v-container class="pl-10 pr-10">
      <v-form ref="form" v-model="valid">
          
        <v-text-field v-model="code" type="number" :counter="5" :rules="codeRules" label="Código *" required></v-text-field>

        <v-text-field v-model="alias" :counter="20" :rules="aliasRules" label="Alias *" required></v-text-field>

        <v-text-field v-model="name" :counter="40" :rules="nameRules" label="Nombre *" required></v-text-field>

        <v-text-field v-model="email" :rules="emailRules" label="E-mail"></v-text-field>

        <v-text-field v-model="idn" :rules="idnRules" label="NIF *" required></v-text-field>

        <v-text-field v-model="address" :counter="200" :rules="addressRules" label="Dirección"></v-text-field>

        <v-text-field v-model="province" :counter="20" :rules="provinceRules" label="Provincia"></v-text-field>

        <v-text-field v-model="telephone" type="number" :counter="15" :rules="telephoneRules" label="Teléfono"></v-text-field>

        <div class="mb-10"></div>

        <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">Crear</v-btn>

        <v-btn color="error" class="mr-4" @click="reset">Cancelar</v-btn>

        <v-btn to="/customer/">Volver</v-btn>

      </v-form>
    </v-container>
  </v-content>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    code: "",
    codeRules: [
      v => !!v || "El código es obligatorio",
      v => (v && v.length <= 5) || "El nombre debe tener un máximo de 5 dígitos"
    ],
    name: "",
    nameRules: [
      v => !!v || "El nombre es obligatorio",
      v =>
        (v && v.length <= 40) || "El nombre debe tener menos de 40 caracteres"
    ],
    alias: "",
    aliasRules: [
      v => !!v || "El alias es obligatorio",
      v => (v && v.length <= 20) || "El alias debe tener menos de 20 caracteres"
    ],
    email: "",
    emailRules: [
        v => (!v || /.+@.+\..+/.test(v)) || "E-mail no válido"
    ],
    idn: "",
    idnRules: [
      v => !!v || "El NIF es obligatorio",
      v => (/^(\d{8})([A-Z])$/.test(v) || /^([ABCDEFGHJKLMNPQRSUVW])(\d{7})([0-9A-J])$/.test(v) || /^[XYZ]\d{7,8}[A-Z]$/.test(v))  || "NIF no válido"
    ],
    address: "",
    addressRules: [
        v => (!v || v.length <= 200) || "La dirección debe tener menos de 200 caracteres"
    ],
    province: "",
    provinceRules: [
        v => (!v || v.length <= 20) || "La provincia debe tener menos de 20 caracteres"
    ],
    telephone: "",
    telephoneRules: [
        v => (!v || v.length <= 15) || "El teléfono debe tener menos de 15 dígitos"
    ],
  }),

  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        //this.snackbar = true;
        // Rest call to create new customer
      }
    },
    reset() {
      this.$refs.form.reset();
    }
  }
};
</script>