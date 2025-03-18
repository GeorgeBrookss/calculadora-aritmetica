





<script setup>

  import { computed, reactive } from 'vue';

const operacaoAtual = reactive({
  tipo: 'Somar'
})


const operacoes = {
  Somar: (a, b) => a + b,
  Subtrair: (a, b) => a - b,
  Multiplicar: (a, b) => a * b,
  Dividir: (a, b) => b !== 0 ? a / b: 'erro',
}

const numeros = reactive({
  numero1: 0,
  numero2: 0,
  
})


const resultadoOperacao = computed(() => {
  const operacao = operacoes [operacaoAtual.tipo];
  return operacao ?operacao(numeros.numero1, numeros.numero2): 0;
});








</script>

<template>
  
  <header>
    <div class="row">
    <div class="col container">
        <h1 class="bg-light mb-5">Bem-vindo a Calculadora Aritmética</h1>
    </div>
    </div>
    <div class="row">
    <div class="col container">
        <input  @keyup="evento => numeros.numero1 = +evento.target.value" class="form-control" placeholder="Digite Aqui o Primeiro Valor" type="number">
    </div>
    <div class="col">
        <input  @keyup="evento => numeros.numero2 = +evento.target.value" class="form-control" placeholder="Digite Aqui o Segundo Valor" type="number" >
    </div>
    </div>
</header>

  <div class="row">
    <div class="col select">
      <select v-model="operacaoAtual.tipo" class="btn btn-dark">
        <option>Somar</option>
        <option >Subtrair</option>
        <option >Multiplicar</option>
        <option>Dividir</option>
      </select>
    </div>
  </div>

  <div class="row">
    <div class="col mt-5 resultado">
      <h3>Resultado: </h3>
      <span v-if="operacaoAtual.tipo === 'Somar'">
      {{ numeros.numero1 }} + {{ numeros.numero2 }} = {{ resultadoOperacao }}
    </span>
    <span v-if="operacaoAtual.tipo === 'Subtrair'">
      {{ numeros.numero1 }} - {{ numeros.numero2 }} = {{ resultadoOperacao }}
    </span>
    <span v-if="operacaoAtual.tipo === 'Multiplicar'">
      {{ numeros.numero1 }} * {{ numeros.numero2 }} = {{ resultadoOperacao }}
    </span>
    <span v-if="operacaoAtual.tipo === 'Dividir'">
      {{ numeros.numero1 }} / {{ numeros.numero2 }} = {{ resultadoOperacao }}
    </span>
    </div>
  </div>


</template>

<style scoped>

*{
  max-width: 1024px;
}


.container{
  margin: 0 auto;
  text-align: center;
}

.select{
  text-align: center;
  margin-top: 20px;
}

.resultado{
  text-align: center;
}


</style>
