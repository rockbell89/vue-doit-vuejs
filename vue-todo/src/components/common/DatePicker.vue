<template lang="html">
  <div class="calendarContainer">
    <span class="icon-calendar">
      <i class="fas fa-calendar-alt"></i>
    </span>
    <input type="text" id="calendar" placeholder="날짜를 선택해주세요." :value="value" @input="updateDate()">
    {{ value }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: '',
    }
  },
  methods: {
    updateDate() {
      this.$emit('input', value);
    }
  },
}
</script>

<style lang="css" scoped>
  .calendarContainer {display: -webkit-flex;  display: -ms-flex;  display: flex; align-items: center; margin: 1rem; padding:0rem 1rem; border: 2px solid #41b883; height:50px;  line-height: 50px; background-color: #fff;}
  .calendarContainer .icon-calendar {}
  .calendarContainer input {width:100%; border-style: none; outline:none; padding: 1rem; box-sizing: border-box;}
</style>
