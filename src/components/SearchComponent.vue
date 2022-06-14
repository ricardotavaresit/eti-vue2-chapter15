<template>
  <div>
    <form v-on:submit.prevent="onSubmmit">
      <input type="text" placeholder="CEP" v-model="cep"/>
      <button type="submit" >Search</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Hi",
      cep: "",
    };
  },
  methods: {
    onSubmmit() {
      alert("oi" + this.cep);
    },
  },
};
</script>