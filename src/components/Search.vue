<template>
  <form @submit="handleSubmit">
    <input class="border py-2 px-3 rounded-md text-grey-darkest" v-model="value" placeholder="Pokemon Name" required>
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
