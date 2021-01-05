<template>
  <div>
    <img v-if="data && data.sprites && data.sprites.front_default && !error" :src="data.sprites.front_default" />
    <p v-if="error">Please enter a valid Pokemon</p>
  </div>
</template>

<script>

export default {
  name: "PokeCard",
  props: {
    data: {},
    error: Boolean,
  },
}
</script>



