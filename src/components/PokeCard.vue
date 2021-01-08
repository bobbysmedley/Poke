<template>
  <div class="w-full md:w-1/2 md:justify-start">
    <div v-if="!!data " class="bg-white shadow-xl rounded md:justify-start mx-auto md:ml-14 mt-8 w-52 h-96 border border-solid border-gray-50">
      <div class="photo-wrapper p-2 flex justify-center mt-6">
          <img  :src="data.sprites.front_default" />
      </div>
      <div class="p-2">
        <h3 class="text-center text-xl text-gray-900 font-medium leading-8"><h2> {{ data.name }} </h2></h3>
        <div class="text-center text-gray-400 text-xs font-semibold">
          <span>No: {{ data.id }} </span>
        </div>
        <table class="text-xs my-3 flex justify-center">
          <tbody>
            <tr>
                <td class="px-2 py-2 text-gray-500 font-semibold ">Type</td>
                <td class="px-2 py-2 text-sm font-medium py-1 px-2 rounded align-middle">{{ types }}</td>
            </tr>
            <tr>
                <td class="px-2 py-2 text-gray-500 font-semibold">HP</td>
                <td class="px-2 py-2 text-sm font-medium py-1 px-2 rounded align-middle"> {{ this.data.stats[0].base_stat }} </td>
            </tr>
            <tr>
                <td class="px-2 py-2 text-gray-500 font-semibold">Att</td>
                <td class="px-2 py-2 text-sm font-medium py-1 px-2 rounded align-middle">{{ this.data.stats[1].base_stat }}</td>
            </tr>
            <tr>
                <td class="px-2 py-2 text-gray-500 font-semibold">Def</td>
                <td class="px-2 py-2 text-sm font-medium py-1 px-2 rounded align-middle">{{ this.data.stats[2].base_stat }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PokeCard",
  props: {
    data: Object,
    error: Boolean,
  },
  data() {
    return {
      typeTextColor: "",
      typeBgColor: ""
    }
  },
  computed: {
    types() {
      return this.data.types.map(type => type.type.name).join(", ");
    },
    moves() {
      return this.data.moves.map(move => move.move.name);
    }
  }
}
</script>



