<template>
  <div class="app">
    <h1>Testando essa lista aqui</h1>  
    <div v-for="(poke,index) in pokemons" :key="index"> 
      <Pokemon :name="poke.name" :url="poke.url" :num="index+1" />
    </div>  
  </div>
</template>

<script>

import axios from 'axios';
import Pokemon from '../components/Pokemon';

export default ({
  name: 'App',
  data() {
    return {
      pokemons: []
    }
  },
  components: {
    Pokemon
  },
  created: function() {
    axios.get('https://pokeapi.co/api/v2/pokemon').then(res => {
      console.log('Peguei toda lista');
      this.pokemons = res.data.results
    })
  }
});

</script>