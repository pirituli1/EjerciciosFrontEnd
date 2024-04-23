<script>
import { toHandlers } from 'vue';

export default {
  data() {
    return {
      value: '', // Valor recibido de nuestro input
      res: '', // Resultado de nuestra operación
      msg: '¡Hora de saber si su número es primo o no!', // mensaje de arriba
      statusBoton: false, // para bloquear el botón
      statusReset: true,
      classButtonStart: '',
      classButtonReset: '',
    };
  },
  methods: {
    // Al entrar a la función Main, configurar isLoading() = true
    // tranformar check primo a una función Async y una vez resuelta la función 'isLoading()' = false.
    main(){ // función main de nuestro ejercicio
      this.res =''
      let valorUsuario = this.value; // guardamos el valor del usuario en nuestra constante
      this.checkprimo(valorUsuario)
    },
    checkprimo(valor) {
  if (!valor) {
    this.res = `No pusiste nada. \n Vuelve a intentarlo.`;
    this.resetValue();
    return;
  } else if (isNaN(valor)) {
    this.res = 'No insertaste un número \n Vuelve a intentarlo';
    this.resetValue();
    return;
  } else {
    valor = parseInt(valor);
    switch (true) {
      case valor === 0:
        this.res = `Tu número no puede ser 0`;
        this.resetValue();
        break;
      case valor < 0:
        this.res = `Tu número no puede ser menor a 0`;
        this.resetValue();
        break;
      default:
        this.checkNum(valor);
        break;
    }
  }
  },
  checkNum(valor){
    // Checar si el número es primo o no
    let raiz = Math.floor(Math.sqrt(valor)) + 1;
    for (let i = 2; i < raiz; i++) {
      if (valor % i === 0) {
        this.statusBoton = true;
        this.statusReset = false;
        return this.res = 'valor NO primo';
      }
    }
    this.statusBoton = true;
    this.statusReset = false;
    return this.res = 'valor primo';
    },
  resetValue(){
    // Nos permitirá resetear value
    this.value='';
  },
  buttonReset(){
    this.resetValue();
    this.res = '';
    this.msg = 'Prueba con un nuevo número. Para saber números primos'
    this.statusBoton = false;
    this.statusReset = true;
  },
  editVar(element,value){
    this.element = value;
  },

  }
}
</script>

<template>
  <h1> {{ msg }} </h1>
  <input type="text" v-model="value" placeholder="Escriba su número primo..."> <br>
  <!-- Cambiar StatusBoton a IsLoading -->
  <button @click="main()" :disabled="statusBoton" class = "buttonAllow">Comprobar</button> <button @click="buttonReset()" :disabled="statusReset" :class = classButtonReset> Reset </button>
  <br> <p> {{ res }}</p>


</template>



<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

</style>
