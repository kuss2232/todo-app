<template>
  <div>
    <li v-for="(todoItem, index) in propsdata" v-bind:key="index">
      {{ todoItem }}
      <button v-on:click="removeItem(todoItem, index)">remove</button>
    </li>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods: {
    removeItem: function(todoItem, index) {
      this.$emit('remove', todoItem, index);
      //todoItems.splice(index, 1);
      //this.localStorage.removeItem();
    },
  },
};
</script>

<style></style>
