<script>
export default {

  data() {
    return {
      firstname: '',
    };
  },
  methods: {
    addOne() {
      this.$emit('addOne', this.firstname);
    },
  },
};
</script>

<template>
<div>
  <input type="text" v-model="firstname" placeholder="prenom">
  <button v-on:click="addOne">Ajouter</button>
</div>
</template>

<style>

</style>
