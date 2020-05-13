<template>
  <div>
    <!-- <p>{{ msg }}</p>
    <main v-if="show">메인</main>-->
    <todo-header></todo-header>
    <todo-input v-on:add="addItem"></todo-input>
    <todo-list
      v-bind:propsdata="todoItems"
      v-on:remove="removeItem"
    ></todo-list>
    <todo-footer v-on:clear="clearTodo"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from '@/components/TodoList.vue';
import TodoFooter from '@/components/TodoFooter.vue';

export default {
  components: {
    'todo-header': TodoHeader,
    'todo-list': TodoList,
    'todo-input': TodoInput,
    'todo-footer': TodoFooter,
  },

  data() {
    return {
      todoItems: [],
    };
  },

  methods: {
    addItem: function(text) {
      this.todoItems.push(text);
    },
    removeItem: function(todoItem, index) {
      this.todoItems.splice(index, 1);
      localStorage.removeItem(todoItem);
    },
    fetchTodoItems: function() {
      for (var i = 0; i < localStorage.length; i++) {
        var value = localStorage.key(i);
        this.todoItems.push(value);
      }
    },
    clearTodo: function() {
      localStorage.clear();
      this.todoItems = [];
    },
  },
  created: function() {
    this.fetchTodoItems();
  },
};
</script>

<style></style>
