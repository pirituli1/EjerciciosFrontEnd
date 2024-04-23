<script>
// import sprigatitoImg from './imgsrc/tarjetasPokemon/sprigatito.png';
// import golisopodImg from './imgsrc/tarjetasPokemon/golisopod.png';
// import goodraImg from './imgsrc/tarjetasPokemon/goodra.png';

import * from './imgsrc/tarjetasPokemon'
export default {
  data() {
    return {
    };
  },
  methods: {
    getPokemonImgSrc(pokemonName) {
      switch (pokemonName) {
        case 'sprigatito':
          return sprigatitoImg;
        case 'golisopod':
          return golisopodImg;
        case 'goodra':
          return goodraImg;
        // Agrega los demás casos para los pokemones aquí
        default:
          return null; // Manejar el caso cuando no hay una imagen para el pokemon
      }
    }
  }
};
</script>
