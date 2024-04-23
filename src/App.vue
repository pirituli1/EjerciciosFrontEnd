<script>
export default {
  data() {
    return {
      manzana: null,
      carrito: 0,
      cantidadManzanas: 0,
    };
  },
  computed: {
    totalCarrito() {
      this.carrito = this.cantidadManzanas * this.manzana
      return this.carrito = this.carrito.toFixed(2)
    },
    warning() {
      if (this.manzana >= 99.99) {
        return 'Sobrepasado del número aceptado. Precio máximo:$99.99';
      } else {
        return '';
      }
    }
  },
  methods: {
    manzanaAdd() {
      this.cantidadManzanas++;
    },
    manzanaRest() {
      if (this.cantidadManzanas > 0) {
        this.cantidadManzanas--;
      }
    }
  },
};
</script>


<template>
  <div>
    <h1 class="title">Bienvenido a la tienda donde tú pones tu precio!</h1>
    <span>¡Agrega el precio y lleva tus manzanas!</span>
    <img src="https://static.vecteezy.com/system/resources/previews/027/190/629/original/pixel-art-red-apple-character-2-png.png" class="imgManzana"><br>
        <span>Precio Actual Manzana: ${{ manzana}} <br> Carrito: ${{ totalCarrito }} <br> Cantidad:{{ cantidadManzanas }} </span><br>
    <button class="botonCarritoAdd" @click="manzanaAdd">Agregar al carrito +1</button><br>
    <button class="botonCarritorRemove" @click="manzanaRest">Quitar al carrito -1</button>
      Precio actual de las manzanas:<input type="text" name="Manzanas" maxlength="5" placeholder="Precio maximo 99.99" v-model="manzana"> {{ warning }}
  </div>
</template>


<style>
body{
  padding-top: 50px;
  padding-right: 50px;
  padding-bottom: 50px;
  padding-left: 50px;
}
.title{
  color:red;
}
.imgManzana{
  height: 200px;
  width: auto;
}
.botonCarritoAdd{
  height: auto;
  width: auto;
  background-color: green;
  text-decoration-line: underline;
  text-decoration-color: black;
}
.botonCarritorRemove{
  height: auto;
  width: auto;
  background-color: red;
  text-decoration-line: underline;
  text-decoration-color: black;
}
</style>