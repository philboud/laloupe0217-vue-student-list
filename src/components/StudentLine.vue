<script>
  export default {
    props: ['student'],
    methods: {
      remove() {
        this.$emit('remove');
      },
    },
  };
</script>

<template lang="pug">
  div
    | {{student.firstname}}
    button(@click="remove") Supprimer
</template>

<style>
</style>
