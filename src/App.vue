<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    numeros:{
      primeiroNumero: "",
      segundoNumero: "",
    },

    options: {
      operacao: "",
    },

    resultado: null
  })

  const recuperarPrimeiroNumero = (e) => {
    estado.primeiroNumero = e.target.value
  }
  const recuperarSegundoNumero = (e) => {
    estado.segundoNumero = e.target.value
  }

  const calcularNumeros = () => {
    const {primeiroNumero, segundoNumero} = estado
    const num1 = parseInt(primeiroNumero)
    const num2 = parseInt(segundoNumero)

      if(estado.options.operacao == "somar"){
        estado.resultado = num1 + num2
      }
      else if(estado.options.operacao == "subtrair"){
        estado.resultado = num1 - num2
      }
      else if(estado.options.operacao == "dividir"){
        estado.resultado = num1 / num2
      }
      else{
        estado.resultado = num1 * num2
      }
  }
</script>

<template>
  <main>
    <h1>Calculadora</h1>
  
    <input class="inputControl" type="number" @keyup="recuperarPrimeiroNumero">
    <input class="inputControl" type="number" @keyup="recuperarSegundoNumero">

    <select v-model="estado.options.operacao" @change="calcularNumeros">
      <option value="somar">somar</option>
      <option value="subtrair">subtrair</option>
      <option value="dividir">dividir</option>
      <option value="multiplicar">multiplicar</option>
    </select>

    <span>{{ estado.resultado }}</span>
  </main>
</template>

<style scoped>

  main{
    height: 100vh;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 1rem;

    font-family: Arial, Helvetica, sans-serif;
  }
  .inputControl{
    width: 4rem;
    height: 2rem;
  }

  select{
    height: 2rem;
    font-weight: bold;
  }
</style>
