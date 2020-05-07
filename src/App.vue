<template>
  <div id="app">
    <Calculator></Calculator>
  </div>
</template>
  <script>
  name:'app'
  import Calculator from '@/components/Calculator.vue';
  export default {
    components:{
      Calculator,
    }
  }
  
  </script>
<style>
  body{
    background-image: url('https://cdn.pixabay.com/photo/2018/08/04/11/32/writing-pad-3583553_960_720.jpg');
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
</style>
