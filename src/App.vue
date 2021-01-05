<template>
  <h1>Pokedex</h1>
  <Search @onSubmit="handleSubmit" />
  <poke-card :error="pokeError" :data="data" />
</template>

<script>
import Search from './components/Search.vue';
import PokeCard from './components/PokeCard.vue';
import { getPokemon } from './services';

export default {
  name: 'App',
  components: {
    Search,
    PokeCard,
  },
  data() {
    return {
      data: {},
      pokeError: false,
    };
  },
  methods: {
    async handleSubmit(value) {
      try {
        const data = await getPokemon(value);
        this.pokeError = false;
        this.data = data;
      } catch {
        this.pokeError = true;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
