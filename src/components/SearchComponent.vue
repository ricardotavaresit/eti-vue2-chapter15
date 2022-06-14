<template>
  <div>
    <form v-on:submit.prevent="onSubmmit">
      <input type="text" placeholder="CEP" v-model="cep" />
      <button type="submit">Search</button>
    </form>
    <div v-if="preLoader">
      <img class="pre-loader" src="./../assets/Swing-Preloader.svg" />
    </div>
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
      preLoader: false,
    };
  },
  methods: {
    onSubmmit() {
      this.preLoader = true;
      axios
        .get(`https://viacep.com.br/ws/${this.cep}/json`)
        .then((response) => {
          this.adress = response.data;
          console.log(this.adress);
        })
        .catch((error) => console.error(error))
        .finally(() => (this.preLoader = false));
    },
  },
};
</script>


<style scoped>
.pre-loader {
  max-width: 100px;
}
</style>