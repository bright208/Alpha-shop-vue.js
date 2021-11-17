<template>

<section class="product-container">
    <h3 class="product-title">購物籃</h3>
    <div class="render-box">
      <h1 class="empty-cart" v-show="products.length===0">Oops 您的購物車是空的!</h1>
      <div v-for="product in products" :key="product.id" class="product-item">
      <div class="product-photo">
        <img :src="product.image" alt="">
      </div>
      <div class="product-info">
        <h5 class="item-name">{{product.name}}</h5>

        <div class="item-count">
        <i class="fas fa-plus-circle" v-on:click="addCount(product.id)"></i>
         <span>   {{product.count}}   </span>
          <i class="fas fa-minus-circle" v-on:click="minusCount(product.id)"></i></div>
        <div class="item-price"> {{product.price}}</div>
      </div>
    </div>
    </div>
    <div class="shipping-cost">
      <span class="shipping-cost-title">運費</span>
      <span class="shipping-cost-number">
         {{(initialshippingCost===0)? "限時免費!":initialshippingCost}}
      </span>
    </div>
    <div class="subtotal">
      <span class="subtotal-title">小計</span>
      <span class="subtotal-number">
        {{sum | currencyFormat}}
      </span>
    </div>
  </section>

</template>

<script>
import currencyFormatter from 'currency-formatter'


 const dummyProduct = [
  { 
    id:1,
    image: "https://i.ibb.co/TP7Z9jp/2.jpg",
    name: "郭雪芙 One boy 衝鋒衣",
    count: 1,
    price: 3999
  },
  { 
    id:2,
    image: "https://i.ibb.co/RPgZ8h1/image.jpg",
    name: "周曉涵 All in one 輕峰衣",
    count: 1,
    price: 1299
  },
  {
    id:3,
    image:
      "https://i.ibb.co/grs20PY/one-boy-1601450187-a71bfb76-progressive.jpg",
    name: "One boy 輕量防風薄衝鋒衣 ",
    count: 1,
    price: 2999
  }
]



export default{
   props:{
     initialshippingCost:{
       type:Number,
       required:true
     }
   },
   data(){
    return{
      products:[],
      sum:0
    }
   },
   methods:{
     fetchProducts(){
     this.products=[...dummyProduct].map(product=>{
      return {...product,pricecached:product.price}
       }
     )
     
     },
     fetchShipCost(){
      this.shipCost=this.initialshippingCost
     },
     addCount(id){
       this.products=this.products.map(product=>
        {
          if(product.id===id){
         return  {...product,count:product.count+1}         
          }
          else{
            return product
          }
       }
       )
       this.caculatePrice()
     },
     minusCount(id){
      this.products=this.products.map(product=>
        {
          if(product.id===id&&product.count!==0){
          return  {...product,count:product.count-1}
        }
        else{
          return product
        }
        })
       this.deleteItem(id) 
       this.caculatePrice()
     },
     deleteItem(id){
       if(this.products.some(product=>product.count===0)){
         let index=this.products.findIndex(product=>product.id===id)
        this.products.splice(index,1)         
        }
     },
     caculatePrice(){
       this.products=this.products.map(product=>{
        return {...product,price:product.count*product.pricecached}
       })
       this.sum=0
       for(let i=0;i<this.products.length;i=i+1){
           this.sum+=this.products[i].price
         }
         this.sum+=this.initialshippingCost
       } 
   },
   filters:{
     currencyFormat(amount){
    return  currencyFormatter.format(amount, { code: 'TWD'});
     }
   },
   created(){
     this.fetchProducts()     
     this.caculatePrice()
   },
   watch:{
     initialshippingCost(){
       this.caculatePrice()
     }
   }

  

}

</script>