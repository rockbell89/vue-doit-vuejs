<template lang="html">
  <div class="">
    <div class="inputBox shadow">
      <input type="text" name="" value="" placeholder="할일 내용을 입력해주세요." v-model="newTodoItem" v-on:kyeup.enter="addTodo">
      <!-- <button type="button" name="button" v-on:click="addTodo">추가</button> -->
      <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fas fa-plus" aria-hidden="true"></i>
      </span>
      <modal v-if="showModal" @close="showModal = false">
        <h3 slot="header">경고</h3>
        <span slot="footer" @click="showModal = false">
          할 일을 입력하세요.
          <i class="closeModalBtn fas fa-times"></i>
        </span>
      </modal>
    </div>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'
import DatePicker from './common/DatePicker.vue'

export default {
  components: {
    'Modal': Modal
  },
  data() {
    return {
      newTodoItem: '',
      showModal: false
    }
  },
  methods: {
    addTodo() {
      if(this.newTodoItem !== ""){
        var value= this.newTodoItem && this.newTodoItem.trim();
        // localStorage.setItem(value, value);
        this.$emit('addTodo', value)
        this.clearInput();
      }else{
        this.showModal = !this.showModal;
      }

    },
    clearInput() {
      this.newTodoItem = ''; // 내용초기화
    }
  }
}
</script>

<style lang="css" scoped>
  .calendarContainer {display: -webkit-flex;  display: -ms-flex;  display: flex; align-items: center; margin: 1rem; padding:0rem 1rem; border: 2px solid #41b883; height:50px;  line-height: 50px; background-color: #fff;}
  .calendarContainer .icon-calendar {}
  .calendarContainer input {width:100%; border-style: none; outline:none; padding: 1rem; box-sizing: border-box;}
  .inputBox {position: relative; background-color: #fff; height: 50px; line-height: 50px; border-radius: 3px; overflow: hidden; padding-right: 3rem; margin: 1rem;}
  .inputBox input:focus {outline:0;}
  .inputBox input {width:100%; border-style: none; font-size: 0.9rem; padding: 1rem; box-sizing: border-box;}
  .inputBox.shadow {box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.1);}
  .addContainer {display: block; position: absolute; top:0; right: 0; background-color: #35495e; width:3rem; line-height: 50px; text-align: center; cursor: pointer;}
  .addBtn {color: #fff; vertical-align: middle;}
</style>
