<script>
export default {
  data() {
    return {
        ok: true,
      pokemons: [],
      pokemonsAPI: [
        'https://pokeapi.co/api/v2/pokemon/sprigatito',
        'https://pokeapi.co/api/v2/pokemon/golisopod',
        'https://pokeapi.co/api/v2/pokemon/goodra',
        'https://pokeapi.co/api/v2/pokemon/victreebel',
        'https://pokeapi.co/api/v2/pokemon/victreebel',
        'https://pokeapi.co/api/v2/pokemon/cyndaquil',
        'https://pokeapi.co/api/v2/pokemon/milotic',
        'https://pokeapi.co/api/v2/pokemon/cranidos',
        'https://pokeapi.co/api/v2/pokemon/bulbasaur',
      ],
    };
  },
  mounted() {
    this.promesas();
  },
  methods: {
    promesas(){
        this.pokemons = []
        this.pokemonsAPI.forEach( async(url) => {
            try {
                let data = await fetch(url);
                let pokemon = await data.json()
                this.setPokemonInfo(pokemon); //Retornar un pokemon con los datos necesarios
            } catch (error) {
                this.ok = false
                return this.pokemons = [];
            }
        })
    },
    setPokemonInfo({name, weight, height, abilities, sprites }){
        let img = sprites.front_default
        let habilidad1 = abilities[0] ? abilities[0].ability.name : ''
        let habilidad2 = abilities[1] ? abilities[1].ability.name : ''

        this.pokemons.push({name, weight, height, habilidad1, habilidad2, img})
        return
    },
    pesoKilogramos(peso){
      peso = peso / 10;
      return(peso);
    },
    }
  }
</script>

<template>
    <div v-if="ok" class="tarjeta-container">
        <div v-for="pokemon in pokemons" :key="pokemon.name" class="tarjeta">
            <div class="cuerpo">
                <img :src='pokemon.img' alt='Imagen de {{pokemon.nombre}}'>
                <h2 class="titulo">{{ pokemon.name }}</h2>
            </div>
            <div class="pie">
                <p>Altura: {{ pokemon.height }}m</p>
                <p>Peso: {{ pesoKilogramos(pokemon.weight) }}K</p>
                <p>Habilidades:</p>
                <ul>
                    <li v-if="pokemon.habilidad1">{{ pokemon.habilidad1 }}</li>
                    <li v-if="pokemon.habilidad2">{{ pokemon.habilidad2 }}</li>
                </ul>
            </div>
        </div>
    </div>

    <div v-else>
        ALGO SALIO MAL
    </div>

</template>




<style scoped>
.tarjeta-container {

  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-column-gap: 50px;
  grid-row-gap: 51px;
}

.tarjeta {
  border: 1px solid rgb(20, 20, 20);
  border-radius: 15px;
  box-shadow: 2px 2px 8px 4px #d3d3d3d1;
  font-family: sans-serif;
}

.cuerpo {
  background-color: rgb(231, 76, 76);
  padding: 10px;
}

.titulo {
  font-size: 24px;
  padding: 10px;
}

.pie {
  background: #f6f1f7;
  border-radius: 0 0 15px 15px;
  padding: 10px;
}

.pie p {
  text-transform: uppercase;
  font-family: monospace;
}

.pie ul li {
  font-family: monospace;
  list-style: none;
  font-style: italic;
}

.pie ul li {
  padding-left: 1rem;
  background-image: url(./imgsr/pokebola.png);
  background-position: 0 90%;
  background-size: 0.9rem 0.9rem;
  background-repeat: no-repeat;
}

.pie a:after {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1;
  content: "";
}
</style>