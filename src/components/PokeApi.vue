<template>
  <div row>
      <h1>PokeGuía</h1>
      <label for="pokemon"></label>
      <p>Nombre</p>
      <input v-model="pokemonName" type="text">
      <p v-if="error">Su búsqueda no arrojó resultados</p>
      <button @click="searchPokemon" >Buscar</button>
     
      <br>
      <img v-if="currentPokemon.sprites" :src="sprites[this.photoIndex]"/>
      <button @click="photoIndex +=1">
          Previa
      </button>
      <button @click="photoIndex -=1">
          Siguiente
      </button>

      <h3>Moves</h3>
      <ul>
          <li v-for="move in moves" :key="move.name">
              {{move.move.name}}
          </li>
      </ul>
      <h3>Abilities</h3>
      <ul>
          <li v-for="ability in abilities" :key="ability.name">
              {{ability.ability.name}}
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    data() {
        return{
            currentPokemon: {},
            pokemonName: "",
            error: undefined,
            photoIndex: 0,
        }
    },
    created () {
    },
    methods: {
        searchPokemon () {
            fetch (`https://pokeapi.co/api/v2/pokemon/${this.pokemonName}`)
            .then(data => data.json())
            .then(response => {
                console.log(response);
                this.error = undefined;
                return (this.currentPokemon = response); 
                })
                .catch((error) =>(this.error = error))
            }
    },
    computed:{
        moves(){
            return this.currentPokemon.moves
        },
        abilities(){
            return this.currentPokemon.abilities
        },
        lower() {
            return this.pokemonName.toLowerCase()
        },
        sprites(){
            return Object.values(this.currentPokemon.sprites);
        }
    }
}
</script>

<style>

</style>