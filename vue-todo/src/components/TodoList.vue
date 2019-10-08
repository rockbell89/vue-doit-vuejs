<template lang="html">
  <section>
    <transition-group tag="ul" name="list">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
        <i class="checkBtn fas fa-check"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  props: ['propsdata'],
  // data() {
  //   return {
  //     todoItems: [],
  //
  //   }
  // },
  // created() {
  //   if(localStorage.length > 0){
  //     for(var i=0; i <localStorage.length; i++){
  //       this.todoItems.push(localStorage.key(i));
  //     }
  //   }
  // },
  methods: {
    removeTodo(todoItem, index) {
      // localStorage.removeItem(todoItem);
      // if(Array.isArray(this.todoItems) && this.todoItems.length > 0) {
      //   this.todoItems.splice(index, 1);
      // }
      this.$emit('removeTodo', todoItem, index)
    }
  },
}
</script>

<style lang="css" scoped>
  section {margin: 1rem;}
  section ul {margin: 0; padding: 0; list-style-type: none;}
  section ul li {background-color: #fff; padding: 1rem;  display: -webkit-flex;  display: -ms-flex;  display: flex; border-radius: 4px;}
  section ul li + li {margin-top: 1rem;}
  section ul li.shadow {box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.1);}
  section ul li .checkBtn {margin-right: 10px;}
  section ul li .removeBtn {margin-left: auto; color:red; cursor: pointer;}
  .list-enter-active,
  .list-leave-active { transition: all 0.5s;}
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
</style>
