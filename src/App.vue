<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8">
        <div class="row">
          <div class="col-md-4" v-for="product in products" :key="product.id">
            <product
              v-on:add-to-cart="addToCart(product)"
              :product="product"
              :IsInCart="IsInCart(product)"
            ></product>
          </div>
        </div>
      </div>
      <div class="col-md-4">
        <cartcomp
          v-on:remove-from-cart="removeFromCart($event)"
          :items="cart"
          v-on:pay="pay()"
        ></cartcomp>
      </div>
    </div>
  </div>
</template>

<script>
import products from "@/products.json";
import product from "@/components/product.vue";
import cartcomp from "@/components/cart.vue";

export default {
  components: {
    product,
    cartcomp,
  },
  data() {
    return {
      products,
      cart: [],
    };
  },
  methods: {

    addToCart(product) {
      this.cart.push(product);
    },
    IsInCart(product) {
      const item = this.cart.find(item => item.id===product.id);
      if(item) {
        return true;
      } else {
        return false;
      }
    },
    removeFromCart(product) {
     this.cart = this.cart.filter(item => item.id !== product.id);
    },
    pay()
    {
      this.cart=[];
      alert("Pay Now");
    },
  },
};
</script>

<style>
body {
  background-color: #fbf8f3;
}
</style>
