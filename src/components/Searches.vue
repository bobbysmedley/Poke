<template>
  <div v-if="searches.length > 0" class="hidden md:w-1/2 md:flex flex-1 justify-end mt-8 h-96 mr-14 ">
    <div class="w-52 h-full justify-end border border-solid border-gray-50 rounded p-3 bg-white shadow-lg">
      <div class="w-full">
        <p class="w-full text-left font-semibold flex justify-center">Searches</p>
        <ul v-if="searches.length">
          <li v-for="(search, index) in searches" :key="search.id + index" :class="listStyling(search)">
            <button class="px-2 py-1 w-full text-left outline:none" @click="handleClick(index)">
              {{ search.name }}
            </button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
const styles = {
  "electric": "text-yellow-700 bg-yellow-50 hover:bg-yellow-100",
  "normal": "text-gray-700 bg-gray-50 hover:bg-gray-100",
  "fire": "text-red-700 bg-red-50 hover:bg-red-100",
  "grass": "text-green-700 bg-green-50 hover:bg-green-100",
  "water": "text-blue-700 bg-blue-50 hover:bg-blue-100",
  "ice": "text-blue-700 bg-blue-50 hover:bg-blue-100",
  "fighting": "text-red-700 bg-red-50 hover:bg-red-100",
  "poison": "text-purple-700 bg-purple-50 hover:bg-purple-100",
  "ground": "text-yellow-700 bg-yellow-50 hover:bg-yellow-100",
  "psychic": "text-pink-700 bg-pink-50 hover:bg-pink-100",
  "bug": "text-green-700 bg-green-50 hover:bg-green-100",
  "rock": "text-yellow-700 bg-yellow-50 hover:bg-yellow-100",
  "ghost": "text-purple-700 bg-purple-50 hover:bg-purple-100",
  "dark": "text-yellow-700 bg-yellow-50 hover:bg-yellow-100",
  "dragon": "text-indigo-700 bg-indigo-50 hover:bg-indigo-100",
  "steel": "text-indigo-700 bg-indigo-50 hover:bg-indigo-100",
  "fairy": "text-pink-700 bg-pink-50 hover:bg-pink-100",
};

const listItemStyles = "mt-2 text-left cursor-pointer hover:bg-gray-100";

export default {
  name: "Searches",
  props: {
    data: Object,
    searches: Array,
  },
  methods: {
    handleClick(ind) {
      this.$emit('switchData', ind);
    },
    listStyling(search) {
      const type = search.types[0].type.name;

      return `${listItemStyles} ${styles[type]}`;
    }
  },
}
</script>
