<template>
  <v-content>
    <v-container>
      <v-layout text-right wrap class="pb-10 pt-5 mr-5">
        <v-flex xs12>
          <v-btn to="/new-customer/">
            <span>Nuevo</span>
          </v-btn>
        </v-flex>
      </v-layout>
      <v-data-table :loading="!customers || customers.length == 0" loading-text="Cargando... Por favor, espere" :headers="headers" :items="customers" :items-per-page="15">
      </v-data-table>
      <v-layout text-center wrap class="pt-10">
        <v-flex xs12>
          <v-btn to="/">
            <span>Volver</span>
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </v-content>
</template>

<script>
export default {
  name: "customer",
  data: () => {
    return {
      customers: [],
      headers: [
          {text: "Código", sortable: false, value: "code"},
          {text: "Alias", sortable: false, value: "alias"},
          {text: "Nombre", sortable: false, value: "name"},
          {text: "NIF", sortable: false, value: "idn"}
      ]
    };
  },
  created() {
    this.listCustomers();
  },
  methods: {
    listCustomers() {
      // Rest call to list clients
      setTimeout(() => this.customers = [
                { id: 1, code: 1, alias: "CLI1", name: "Cliente 1", idn: "E12434545" },
                { id: 2, code: 2, alias: "CLI2", name: "Cliente 2", idn: "M37457357" }
      ], 1000);
    }
  }
};
</script>