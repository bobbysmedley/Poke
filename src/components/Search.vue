<template>
  <form @submit="handleSubmit">
    <input v-model="value" placeholder="Pokemon Name">
  </form>
</template>


<script>
export default {
  name: "Search",
  data(){
    return {
      value: "",
    };
  },

  methods: {
    handleSubmit(e) {
      e.preventDefault();
        this.$emit("onSubmit", this.value);
        this.value = "";
    },
  },
};
</script>
