<template>
  <div class="card my-5">
      <div class="card-body">
          <h5 class="text-center card-title">
              {{product.title}}
          </h5>
          <p class="text-center card-text text-muted display-4">
              ${{product.price}}
          </p>
          <button :disabled="IsInCart" @click="$emit('add-to-cart',product)" class="btn btn-info form-control">
              {{ IsInCart ? 'Added to Cart' : 'Add To Card'}}
          </button>     
     </div>
  </div>
</template>

<script>
export default {

props:[
    'product',
    'IsInCart'
],
   
}
</script>

<style>

</style>