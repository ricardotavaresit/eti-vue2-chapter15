<template>
  <div>
    <form v-on:submit.prevent="onSubmmit">
      <input type="text" placeholder="CEP" v-model="cep" />
      <button type="submit">Search</button>
      <div v-if="error">{{ error }}</div>
    </form>
    <div v-if="preLoader">
      <img class="pre-loader" src="./../assets/Swing-Preloader.svg" />
    </div>
    <div v-if="address.cep">{{ address }}</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      address: {},
      preLoader: false,
      error: "",
    };
  },
  methods: {
    onSubmmit() {
      this.preLoader = true;
      this.reset();
      
      axios
        .get(`https://viacep.com.br/ws/${this.cep}/json`)
        .then((response) => {
          if (response.data.erro) {
            this.error = "CEP not found";
          } else {
            this.address = response.data;
          }
        })
        .catch((error) => {
          console.error(error);
          this.error = "404";
        })
        .finally(() => (this.preLoader = false));
    },
    reset() {
      this.address = "";
      this.error = "";
    },
  },
};
</script>


<style scoped>
.pre-loader {
  max-width: 100px;
}
</style>