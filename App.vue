<script setup>
import {reactive} from 'vue'

const estado = reactive({
  a: 1,
  b:1,
  choice: '+',
})

const soma = () => {
  return parseFloat(estado.a) + parseFloat(estado.b)
}

const subtracao = () => {
  return estado.a - estado.b
}

const multiplicacao = () => {
  return estado.a * estado.b
}

const dividir = () => {
  return estado.a / estado.b
}

const contas = () => {
  const {choice} = estado
  switch (choice) {
  case '+':
    return soma()
  case '-':
    return subtracao() 
  case 'x':
    return multiplicacao()
  case '/':
    return dividir()
}
}

</script>

<template>
  <div class='container'>

    <h1>Exercício vue.js</h1>

   <input class='campo' :value='estado.a'  @change='event => estado.a = event.target.value' type='number'>

  <select @change='event => estado.choice = event.target.value'>
   <option value='+'>+</option>
   <option value='-'>-</option>
   <option value='x'>*</option>
   <option value='/'>/</option>
  </select>

  <input class='campo' :value='estado.b' @change='event => estado.b = event.target.value' type='number'>

  {{estado.a}}{{estado.choice}}{{estado.b}}={{contas()}}

</div>
</template>

<style scoped>
.container {
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
  padding-top: 68px;
}

input {
  margin: 8px;
   border: 1px solid #000;
   border-radius: 8px;
    
}

select {
    border-radius: 8px;
}
</style>  
