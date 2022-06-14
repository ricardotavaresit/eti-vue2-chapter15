<template>
  <div>
    <form v-on:submit.prevent="onSubmmit">
      <input type="text" placeholder="CEP" v-model="cep" />
      <button type="submit">Search</button>
    </form>
    <div v-if="adress.cep">{{ adress }}</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      adress: {},
    };
  },
  methods: {
    onSubmmit() {
      axios
        .get(`https://viacep.com.br/ws/${this.cep}/json`)
        .then((response) => {
          this.adress = response.data;
          console.log(this.adress);
        })
        .catch((error) => console.error(error));
    },
  },
};
</script>