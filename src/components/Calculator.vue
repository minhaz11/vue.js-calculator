<template>
  <div class="calculator">
      <div class="display">
         <span class="curr">{{current || '0'}}</span> 
      </div>
      <div class="btn " @click="clear">C</div>
      <div class="btn " @click="sign">+/-</div>
      <div class="btn ">%</div>
      <div @click="divide" class="btn operator">÷</div>
      <div @click="append('7')" class="btn ">7</div>
      <div @click="append('8')" class="btn ">8</div>
      <div @click="append('9')" class="btn ">9</div>
      <div @click="times" class="btn operator">×</div>
      <div @click="append('4')" class="btn ">4</div>
      <div @click="append('5')" class="btn ">5</div>
      <div @click="append('6')" class="btn ">6</div>
      <div @click="minus" class="btn operator">-</div>
      <div @click="append('1')" class="btn ">1</div>
      <div @click="append('3')" class="btn ">2</div>
      <div @click="append('4')" class="btn ">3</div>
      <div @click="sum" class="btn operator">+</div>
      <div @click="append('0')" class="btn zero">0</div>
      <div @click="dot()" class="btn ">.</div>
      <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
name:'Calculator'
export default {
    data() {
        return {
            current: '',
            operator:null,
            previous:null,
            operatorClicked:false
        }
    },
    methods: {
        clear() {
            this.current = ''
        },
        sign(){
            this.current = this.current.charAt(0)==='-'? this.current.slice(1):`-${this.current}`
        },
        percentage(){
            this.current = `${parseFloat(this.current)/100}`
        },
        append(number){
            if(this.operatorClicked){
                this.current=''
                this.operatorClicked = false
            }
            this.current = `${this.current+number}`
        },
        setPrevious(){
            this.previous = this.current
            this.operatorClicked = true
        },
        dot(){
            if(this.current.indexOf('.') === -1){
                this.append('.')
            }
        },
        divide(){
            this.operator = (a,b)=>a/b;
            this.setPrevious()
        },
        times(){
            this.operator = (a,b)=>a*b;
            this.setPrevious()
        },
        minus(){
            this.operator = (a,b)=>a-b;
            this.setPrevious()
        },
        sum(){
            this.operator = (a,b)=>a+b;
            this.setPrevious()
        },
        equal(){
            this.current = `${this.operator(
                parseFloat(this.previous),
                parseFloat(this.current)
            )}`
        }
    },
}
</script>

<style>
    .calculator{
        box-shadow: 1px 10px 23px 6px rgba(0,0,0,0.75);
        width: 500px;
        height:520px;
        margin:71px auto;
        font-size:40px;
        display: grid;
        grid-template-columns: repeat(4,1fr);
        grid-auto-rows: minmax(50px,auto);
        border-radius: 10px 10px 10px 10px;
        -moz-border-radius: 10px 10px 10px 10px;
        -webkit-border-radius: 10px 10px 10px 10px;
        border: 0px solid #000000;
    }
    .display{
        grid-column: 1/5;
       background: linear-gradient(to right, rgb(109, 109, 109) 13%, rgb(109, 109, 109) 14%, rgb(56, 56, 56) 100%);
        color:white;
        text-align: center;
        text-align: end;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
         padding-top:15px

    }
    .curr{
        margin-right: 10px;
    }
    .zero{
         grid-column: 1/3;
    }
    .btn{
        background: azure;
        border: 1px solid rgb(99, 93, 93);
        text-align: center;
        cursor:pointer;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;
    }
    .operator{
        background: orange;
        color:white
    }
</style>