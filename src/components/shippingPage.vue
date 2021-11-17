<template>

<div class="billing-info">
      <div class="form-container part-b">
        <h3 class="billing-title">運送方式</h3>
        <div class="standard">
          <input v-on:click="shippingCost(0)" type="radio" name="shipping" value="0" id="shipping-standard" checked>
          <label for="shipping-standard"></label>
          <span class="shipping-day">約3~7個工作天</span>
          <span class="shipping-standard">標準運送</span>
          <span class="shipping-free">免費</span>

        </div>
        <div class="express">
          <input v-on:click="shippingCost(500)" type="radio" name="shipping" value="500" id="shipping-express">
          <label for="shipping-express"> </label>
          <span class="shipping-day">48小時內送達</span>
          <span class="shipping-standard">DHL貨運</span>
          <span class="shipping-free">$500</span>

        </div>
      </div>
    </div>

</template>

<script>

export default{
   props:{
     initialshippingCost:{
       type:Number,
       required:true
     }
   },   
   data(){
     return{
    shipCost:0
     }
   },
   methods:{
    shippingCost(fee){
      this.shipCost=fee
      this.$emit("after-select-shippingType",this.shipCost)
    },
    fecthShippingCost(){
    this.shipCost=this.initialshippingCost
    }
   },
   created(){
     this.fecthShippingCost()
   }
}

</script>