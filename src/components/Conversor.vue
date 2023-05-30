<template>
  <div class="fundo">
    <div class="conversor">
      <h2>{{ moedaA }} Para {{ moedaB }}</h2>
      <input
        type="text"
        class="caixa"
        v-model="moedaA_value"
        v-bind:placeholder="moedaA"
      />
      <input
        type="button"
        class="botao"
        value="Converter"
        v-on:click="converter"
      />
      <h2 v-show="moedaB_value">R$ {{ moedaB_value }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Conversor",
  props: ["moedaA", "moedaB"],
  data() {
    return {
      moedaA_value: "",
      moedaB_value: "",
    };
  },
  methods: {
    converter() {
      let de_para = this.moedaA + "-" + this.moedaB;

      let url = "https://economia.awesomeapi.com.br/last/" + de_para;

      fetch(url) 
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          let cotacao = json.USDBRL["bid"];
          console.log(cotacao);
          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(
            2
          );
        });
    },
  },
};
</script>

<style scoped>
.conversor {
  background-color: #444;
  padding: 40px;
  max-width: 300px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  justify-content: space-around;
  border-radius: 10px;
}
.botao {
  font-family: "Roboto", sans-serif;
  cursor: pointer;
  display: inline-block;
  font-size: 17px;
  font-weight: 500;
  -webkit-box-shadow: none;
  box-shadow: none;
  outline: none;
  border: 0;
  color: #fff;
  border-radius: 3px;
  background-color: #011f42;
  padding: 10px 36px;
  margin-bottom: 10px;
  margin-top: 10px;
}
.caixa {
  -webkit-box-shadow: none;
  box-shadow: none;
  border: 1px solid #a9a5a5;
  padding: 10px 0px 14px 10px;
  color: #111;
}
</style>