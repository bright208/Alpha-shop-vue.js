<template>
<header>
  <div class="brand"><img class="brand-logo" src="https://i.ibb.co/K5LF2x5/Alpha-logo.png" alt="">
    <a href="#"><span class="brand-title">Alpha Shop</span></a>
  </div>
  <div class="hamburger"><a v-on:click.prevent.stop="toggleMenu()" href="#" class="hamburger-icon"><i class="fas fa-bars"></i></a></div>
  <div class="icon-group">
    <a class="search-icon" href="#"><i class="fas fa-search"></i></a>
    <a class="cart-icon" href="#"><i class="fas fa-shopping-cart"></i></a>
    <a class="moon-icon" href="#"><i class="far fa-moon"></i></a>
  </div>
  <nav class="menu" :class="[{active:toggle}]">
    <ul>
      <li><a href="#">男款</a></li>
      <li><a href="#">女款</a></li>
      <li><a href="#">最新消息</a></li>
      <li><a href="#">客製商品</a></li>
      <li><a href="#">聯絡我們</a></li>
    </ul>
  </nav>
</header>

</template>

<script>
export default{

    data(){
      return{
       toggle:false
      }
    },
    methods:{
      toggleMenu(){
        this.toggle=!this.toggle
      }
    } 
}


</script>