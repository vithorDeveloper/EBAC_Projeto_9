<script setup>
  import { reactive } from 'vue';

  const estado = reactive({

    numeros:{
      primeiroNumero: 0,
      segundoNumero: 0,
      operacao: "somar",
      resultado: 0,
    },

  })

  const recuperarPrimeiroNumero = (e) => {
    estado.primeiroNumero = e.target.value
  }
  const recuperarSegundoNumero = (e) => {
    estado.segundoNumero = e.target.value
  }

  const calcularNumeros = () => {
    const num1 = parseInt(estado.numeros.primeiroNumero)
    const num2 = parseInt(estado.numeros.segundoNumero)

    if (isNaN(num1) || isNaN(num2)) {
    estado.numeros.resultado = 0
    return;
  }

      if(estado.numeros.operacao == "somar"){
        estado.resultado = num1 + num2
      }
      else if(estado.numeros.operacao == "subtrair"){
        estado.resultado = num1 - num2
      }
      else if(estado.numeros.operacao == "dividir"){
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
  
    <input v-model="estado.numeros.primeiroNumero" @input="calcularNumeros" class="inputControl" type="number" @keyup="recuperarPrimeiroNumero">
    <input v-model="estado.numeros.segundoNumero" @input="calcularNumeros" class="inputControl" type="number" @keyup="recuperarSegundoNumero">
    
    <select v-model="estado.numeros.operacao" @change="calcularNumeros">
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
