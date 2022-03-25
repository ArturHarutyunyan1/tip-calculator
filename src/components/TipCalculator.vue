<template>
  <div class="container">
      <img src="@/assets/logo.svg" alt="logo">
      <div class="card">
          <div class="row">
              <div class="row-item">
                  <div class="item">
                      <h4 class="title">Bill</h4>
                      <div class="input-line">
                          <img src="@/assets/icon-dollar.svg" class="icon" alt="dollar">
                          <input type="number" v-model="bill" @keyup="count()" class="input" placeholder="142.55">
                      </div>
                  </div>
                  <div class="item">
                      <h4 class="title">Select Tip %</h4>
                      <div class="flex-box">
                          <button @click="setValue" class="tip-button" value="5">5%</button>
                          <button @click="setValue" class="tip-button" value="10">10%</button>
                          <button @click="setValue" class="tip-button" value="15">15%</button>
                          <button @click="setValue" class="tip-button" value="25">25%</button>
                          <button @click="setValue" class="tip-button" value="50">50%</button>
                          <input type="number" v-model="percent" @keyup="count()" class="custom" placeholder="Custom">
                      </div>
                  </div>
                  <div class="item">
                      <h4 class="title">Number of People</h4>
                      <div class="input-line">
                          <img src="@/assets/icon-person.svg" class="icon" alt="person">
                          <input type="number" v-model="person" @keyup="count()" class="input" placeholder="3">
                      </div>
                  </div>
              </div>
              <div class="row-item">
                  <div class="result">
                      <div class="space-btw">
                          <div class="flex-item">
                              <h4>Tip Amount</h4>
                              <p>/ person</p>
                          </div>
                          <div class="flex-item">
                              <h1>${{bill}}</h1>
                          </div>
                      </div>
                      <div class="space-btw">
                          <div class="flex-item">
                              <h4>Total Amount</h4>
                              <p>/ person</p>
                          </div>
                          <div class="flex-item">
                              <h1>${{result}}</h1>
                          </div>
                      </div>
                      <div class="reset">
                          <button @click="resetValues">RESET</button>
                      </div>
                  </div>
              </div>
          </div>
      </div>
      <h3 class="author">Challenge by <a href="https://frontendmentor.io" target="_blank">Frontend Mentor</a> Coded by <a href="https://github.com/ArturHarutyunyan1" target="_blank">Artur Harutyunyan</a></h3>
  </div>
</template>

<script>
export default {
    data(){
        return{
            result: null,
            bill: null,
            percent: null,
            person: null,
        }
    },
    mounted(){
        this.count()
        this.resetValues()
    },
    methods:{
        setValue(e){
            this.percent = e.target.value
        },
        count(){
            this.result = Math.round((this.bill * this.percent) / 100 / this.person)
            if(this.result == Infinity || isNaN(this.result)){
                this.result = 0
            }
        },
        resetValues(){
            this.bill = null
            this.percent = null
            this.person = null
            this.result = null
        }
    }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@700&display=swap');
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    :root{
        --strong-cyan: hsl(172, 67%, 45%);
        --very-dark-cyan: hsl(183, 100%, 15%);
        --dark-grayish-cyan: hsl(186, 14%, 43%);
        --grayish-cyan: hsl(184, 14%, 56%);
        --light-grayish-cyan: hsl(185, 41%, 84%);
        --very-light-grayish-cyan: hsl(189, 41%, 97%);
        --white: hsl(0, 0%, 100%);
    }

    body{
        background: var(--light-grayish-cyan);
        font-family: 'Space Mono', monospace;
    }

    .container{
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .card{
        width: 750px;
        height: 400px;
        margin-top: 50px;
        background: var(--white);
        border-radius: 15px;
    }

    .row{
        display: flex;
    }

    .row-item{
        width: 340px;
        height: 340px;
        margin: 30px auto;
    }

    .row-item:nth-child(2){
        background: var(--very-dark-cyan);
        border-radius: 15px;
    }

    .item{
        margin-bottom: 40px;
    }

    .title{
        padding-left: 7px;
        color: var(--dark-grayish-cyan);
    }

    .input-line{
        width: 97%;
        height: 40px;
        background: var(--very-light-grayish-cyan);
        border-radius: 5px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .input{
        width: 100%;
        height: 100%;
        background: transparent;
        border: none;
        outline: none;
        font-size: 20px;
        color: var(--very-dark-cyan);
        font-weight: 700;
        text-align: right;
        padding-right: 15px;
    }

    .icon{
        padding-left: 15px;
    }

    .flex-box{
        display: flex;
        flex-wrap: wrap;
    }

    .tip-button, .custom{
        width: 100px;
        height: 40px;
        margin: 6px 6px;
        font-size: 23px;
    }

    .tip-button{
        background: var(--very-dark-cyan);
        border: none;
        border-radius: 5px;
        color: var(--white);
        font-weight: 700;
        cursor: pointer;
        transition: 0.3s ease-out;
    }

    .tip-button:hover, .tip-button:focus{
        background: var(--strong-cyan);
        color: var(--very-dark-cyan);
    }

    .custom{
        text-align: center;
        border: none;
        outline: none;
        font-size: 23px;
        font-weight: 700;
        color: var(--very-dark-cyan);
        border-radius: 5px;
        background-color: var(--very-light-grayish-cyan);
    }

    ::placeholder{
        color: var(--very-dark-cyan);
        font-weight: 700;
    }

    .result{
        width: 90%;
        margin: auto;
        display: flex;
        flex-direction: column;
        margin: 25px auto;
    }

    .space-btw{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .flex-item{
        margin-bottom: 30px;
    }

    .flex-item h4{
        color: var(--white);
    }

    .flex-item p{
        color: var(--grayish-cyan);
    }

    .flex-item h1{
        font-size: 40px;
        color: var(--strong-cyan);
    }

    .reset{
        width: 90%;
        height: 50px;
        margin: 70px auto;
    }

    .reset button{
        width: 100%;
        height: 100%;
        background: var(--strong-cyan);
        border: none;
        border-radius: 5px;
        font-size: 23px;
        font-weight: 700;
        color: white;
        transition: 0.3s ease-out;
        cursor: pointer;
    }
    .reset button:hover{
        opacity: 0.9;
    }

    .author{
        transform: translateY(100px);
        text-align: center;
        color: var(--very-dark-cyan);
    }

    a{
        color: var(--strong-cyan);
    }

    @media (max-width: 768px){
        .container{
            height: auto;
        }
        .card{
            width: 90%;
            height: auto;
        }
        .row{
            flex-direction: column;
        }
        .row-item{
            width: 100%;
        }
        .input-line{
            width: 100%;
        }
    }

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
    }

    /* Firefox */
    input[type=number] {
    -moz-appearance: textfield;
    }
</style>
