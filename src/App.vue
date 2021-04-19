<template>
  <div class="content">
    <h1>$</h1>
    <div class="div-converter">
      <span class="p-float-label content">
        <InputText
          id="input-reais"
          type="text"
          v-model="reais"
          :disabled="dolares"
        />
        <label for="input-reais">Quantidade em Reais</label>
      </span>
    </div>

    <div class="div-converter">
      <span class="p-float-label content">
        <InputText
          id="input-cotacao"
          type="text"
          v-model="cotacao"
          :disabled="dolares"
        />
        <label for="input-cotacao">Cotação do Dólar</label>
      </span>
    </div>
    <div class="div-converter">
      <Button label="Limpar" @click="clear" />
      <Button style="margin-left: 1rem " label="Calcular" v-on:click="calculate" />
    </div>
    <div class="div-converter" v-if="dolares">
      <p class="label-result">
        Com {{ reais }} é possível comprar {{ dolares }} a {{ cotacao }} cada
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      reais: null,
      cotacao: null,
      dolares: null,
    };
  },
  methods: {
    calculate: function() {
      this.dolares = (this.reais / this.cotacao).toFixed(2);
    },

    clear() {
      this.reais = null;
      this.cotacao = null;
      this.dolares = null;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.div-converter {
  margin-top: 2rem;
}
.content {
  text-align: center !important;
  display: initial !important;
  margin-bottom: 2px;
}
</style>
