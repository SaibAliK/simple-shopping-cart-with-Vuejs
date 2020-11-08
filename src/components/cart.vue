<template>
  <div class="container my-5">
    <ul class="list-group">
      <li class="list-group-item" v-for="item in items" :key="item.id">
        {{ item.title }} - {{ item.price }}
        <button
          @click="$emit('remove-from-cart', item)"
          class="btn btn-danger badge badg-danger float-right"
        >
          Remove from Cart
        </button>
      </li>
    </ul>
    <div class="card p-3 my-5">
        <h3 class="text-center">${{total}}</h3>
            <button :disabled="items.length===0" @click="$emit('pay')" class="btn btn-success">Pay</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["items"],
  computed:{
      total()
      {
          return this.items.reduce((acc,item)=> acc + Number(item.price),0)
      }
  },
};
</script>

<style>
</style>