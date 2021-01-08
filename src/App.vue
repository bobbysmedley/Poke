<template>
  <h1 class="text-4xl font-bold mb-3">Pokedex</h1>
  <Search @onSubmit="handleSubmit"/>
  <p v-if="pokeError" class="justify-center font-medium text-red-500 text-xs mt-1 ml-1">Please enter a valid Pokemon</p>
  <div class="flex max-w-lg mx-auto">
    <SearchList @switchData="handleSwitchData" :data="data" :searches="searches"/>
    <PokeCard :error="pokeError" :data="data"/>
  </div>
</template>

<script>
import Search from './components/Search.vue';
import SearchList from './components/Searches.vue';
import PokeCard from './components/PokeCard.vue';
import { getPokemon } from './services';

export default {
  name: 'App',
  components: {
    Search,
    PokeCard,
    SearchList
  },
  data() {
    return {
      data: null,
      searches: [],
      pokeError: false,
    };
  },
  methods: {
    handleSwitchData(ind) {
      this.data = this.searches[ind];
    },
    async handleSubmit(value) {
      try {
        const data = await getPokemon(value);
        this.pokeError = false;
        this.data = data;

        const arr = [...this.searches];

        if (this.searches.length >= 8) {
          arr.unshift(data);
          arr.pop();

          this.searches = arr;
          return;
        }

        this.searches = [...arr, data];
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
