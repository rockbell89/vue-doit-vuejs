<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoFooter from './components/TodoFooter.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'


export default {
  props: ['propsdata'],
  components: {
    'TodoHeader': TodoHeader,
    'TodoFooter': TodoFooter,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
  },
  data() {
    return {
      todoItems: [],
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      // if(Array.isArray(this.todoItems) && this.todoItems.length > 0) {
        this.todoItems.splice(index, 1);
      // }
    },
    clearAll() {
        localStorage.clear();
        this.todoItems= [];
    }
  },
  created() {
    if(localStorage.length > 0){
      for(var i=0; i <localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
    // 라이브러리 로딩 확인
    console.log($.fn.jquery);
    console.log($.ui.version)
  },
  mounted() {
    $('#calendar').datepicker();
  }
}
</script>

<style lang="scss">
  body {margin: 0; background-color: #f6f6f6;}
  body * {margin: 0; padding: 0; line-height: 1;}
  input {border-style: groove; width: 200px;}
  button {border-style: groove;}

</style>
