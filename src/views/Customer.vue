<template>
  <v-container>
    <v-layout text-right wrap class="pb-10 pt-5 mr-5">
      <v-flex xs12>
        <v-btn to="/">
          <span>Nuevo</span>
        </v-btn>
      </v-flex>
    </v-layout>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">Código</th>
            <th class="text-left">Alias</th>
            <th class="text-left">Nombre</th>
            <th class="text-left">NIF</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in customers" :key="item.id">
            <td>{{ item.code }}</td>
            <td>{{ item.alias }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.idn }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <v-layout text-center wrap class="pt-10">
      <v-flex xs12>
        <v-btn to="/">
          <span>Volver</span>
        </v-btn>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "customer",
  data: () => {
      return {
          customers: []
      }
  },
  created() {
      this.listCustomers();
  },
  methods: {
    listCustomers() {
        // Rest call to list clients
        this.customers = [
            {id: 1, code: 1, alias: "CLI1", name: "Cliente 1", idn: "E12434545"},
            {id: 2, code: 2, alias: "CLI2", name: "Cliente 2", idn: "M37457357"}
        ]
    }
  }
};
</script>