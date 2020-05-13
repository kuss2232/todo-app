<template>
  <button v-on:click="clearStorage">전체삭제</button>
  <!--<button v-on:click="$emit('clear')">clear</button>-->
</template>

<script>
export default {
  methods: {
    clearStorage: function() {
      this.$emit('clear');
    },
  },
};
</script>

<style></style>
