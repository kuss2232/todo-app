<template>
  <div>
    <input type="text" v-model="inputText" v-on:keyup.enter="addItem" />
    <button v-on:click="addItem">add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
    };
  },
  methods: {
    //app.vue의 todoItems에 추가
    addItem: function() {
      var value = this.inputText;
      this.$emit('add', value);
      localStorage.setItem(value, value);
      this.clearInput();
    },
    clearInput: function() {
      this.inputText = '';
    },
  },
};
</script>

<style></style>
