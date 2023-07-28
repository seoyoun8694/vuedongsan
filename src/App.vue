<template>

  <div class="menu">
    <a v-for="naming in menu" :key="naming">{{ naming }}</a>
  </div>

  <transition name="fade">
    <ModalOpen :ifopen="ifopen" :num1="num1" v-if="ifopen" @close="ifopen=false"/>
  </transition>

  <div class="main"
      v-for="(item, index) in room" :key="index">

    <button class="modal" v-bind:num1="index" @click="ifopen = true; num1=index;">
      {{ item.title }}
    </button>
    <img :src="require(`@/assets/room${ index }.jpg`)"/>
    <p>{{ item.price }}</p>

    <button @click="report[index]++">허위매물신고</button><br>
    <span>신고수: {{report[index]}}</span>
  </div>

</template>

<script>
  import oneroom from './data/oneroom.js';
  import ModalOpen from './components/ModalOpen.vue';
  oneroom;

  export default{
    name: 'App', 
    components: {
      ModalOpen
    },

    data(){
      return{
        menu : ['Home', 'Shop', 'About'],
        report : [0,0,0,0,0,0],
        room : oneroom,
        ifopen : false,
      }
    }
  }
</script>

<style>
img{
  width: 100%;
  margin-top: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  width: 100%;
  position: fixed;
  margin-top: -5px;
}
.menu a{
  color : white;
  padding: 10px;
}
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
.modal{
  background: transparent;
  border: transparent;
  font-size: 18px;
  font-weight: bold;
  margin-top: 10px;
}
.main{
  margin-top: 5px;
  padding-top: 55px;
}

.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}


button{
  margin-bottom: 5px;
}
</style>