<template>

    <div class="black-bg">
      <div class="white-bg">
        <img src="">
        <h4>{{ room[num1].title }}</h4>
        <p>{{ room[num1].content }}</p>
        <button @click="$emit('close')">닫기</button>
      </div>
    </div>
  </template>
  
  <script>
  import oneroom from '../data/oneroom.js';
  export default {
      data(){
        return{
          room: oneroom
        }
      },

      props : {
        num1: Number
      },
      
      methods: {
      }
  
  }
  </script>
  
  <style scoped>
  body{
    margin: 0;
  }
  div{
    box-sizing: border-box;
  }
  .black-bg{
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.5);
    position: fixed; padding: 20px;
  }
  .white-bg{
    width: 100%; background: white;
    border-radius: 8px;
    padding: 20px;
  }
  </style>