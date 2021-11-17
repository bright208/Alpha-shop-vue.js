<template>

<main class="container">


<section class="billing-container">
    <h3 class="billing-title">結帳</h3>
    <div class="billing-stepper">
      <div class="step" :class="[{active:step===0},{checked:step>0}]">
        <div class="circle-container"></div>
        <div class="label-container">寄送地址</div>
      </div>
      <div class="step" :class="[{active:step===1},{checked:step>1}]">
        <div class="circle-container"></div>
        <span class="connect-line"></span>
        <div class="label-container">運送方式</div>
      </div>
      <div class="step" :class="[{active:step===2}]">
        <div class="circle-container"></div>
        <span class="connect-line"></span>
        <div class="label-container">付款資訊</div>
      </div>
    </div>

    <!--表單區域-->
    <formPage   v-show="step===0"/>
    <shippingPage :initialshippingCost=shippingCost  v-on:after-select-shippingType="updateCost" v-show="step===1"/>
    <paymentPage  v-show="step===2"/>

    <!--按鈕區域-->
     <div class="button-container" :class="[{active:step===0}]">
      <button class="btn btn-outline" v-show="step!==0" v-on:click="prevStep()">← 上一步</button>
      <button class="btn btn-primary" :class="[{active:step===0}]" v-on:click="nextStep()"> 
      {{ (step===2)? "確認送出":"下一步 →" }}
      </button>
    </div>

  </section>

<!--購物車區域 -->
<shoppingCart :initialshippingCost=shippingCost  />

</main>

</template>

<script>

import formPage from '../components/formPage.vue'
import shoppingCart from '../components/shoppingCart.vue'
import shippingPage from '../components/shippingPage.vue'
import paymentPage from '../components/paymentPage.vue'


export default{
     data(){
     return {
      step:0,
      shippingCost:0 
      }
     },    
    components:{
      formPage:formPage,
      shoppingCart:shoppingCart,
      shippingPage:shippingPage,
      paymentPage:paymentPage      
    },
    methods:{
    nextStep(){
      if(this.step<2){
        this.step=this.step+1
      }      
    },
    prevStep(){
      this.step=this.step-1      
    },
    updateCost(fee){
     this.shippingCost=fee
    }
  
    }
}

</script>