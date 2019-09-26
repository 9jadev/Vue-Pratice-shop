<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
       <div class="row">
         <div :key="product.id" class="col-md-6" v-for="product in products">
           <product :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"> </product>
         </div>
       </div>
      </div>
      <div class="col-md-5 my-5">
        <cart :items="cart" v-on:remove-from-cart="removeFromCart($event)"></cart>
        <hr>
        <p class="lead">
          Total: <b class="float-right"> {{newtotal}}</b>
        </p>
        
      </div>
    </div>
  </div>
</template>

<script>
import products from '@/product.json';
import product from '@/components/Product.vue';
import Cart from '@/components/Cart.vue';
export default {
  name: 'app',
  components: {
    product,
    Cart
  },
  data(){
    return{
      products,
      cart: [],
      total : 0,
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
      
      this.total += parseInt(product.price);
    },
    isInCart(product){
      const item = this.cart.find(item => item.id === product.id);
      if (item) {
        return true;
      }
      return false;
    },
    removeFromCart(product){
      this.cart = this.cart.filter(item => item.id !== product.id);
    }
  },
  computed:{
    newtotal(){
      return Number(this.total).toFixed(2);
    }
  } 
}
</script>

<style>
  body{
    background: #f0ffff73;;
  }
</style>
