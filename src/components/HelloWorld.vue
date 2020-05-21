<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Bienvenido a {{ nameApp }}
        </h1>
      </v-col>
      <v-col class="mb-4">
        <p>Usuario generado: {{ userRandom }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      nameApp: "user-random",
      userRandom: null,
    };
  },
  mounted() {
    // console.log("Hola desde mounted");
    this.getUsers();
  },
  methods: {
    getUsers() {
      // console.log("Hola desde methods");
      axios
        .get("https://randomuser.me/api/")
        .then((res) => {
          // console.log(res.data.results);
          this.userRandom = res.data;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>
