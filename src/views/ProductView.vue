<template>
  <main class="wrapper">
    <h1>Products</h1>
    <div class="card-container">

      <ProductCard v-for="(product, index) in inventory" class="card" :key="product.id" :index="index"
        :product="product" :addToCart="addToCart" :getClass="getClass" />

    </div>
  </main>
</template>
<script>
import ProductCard from '@/components/ProductCard.vue'
// @ is an alias to /src
export default {
  // eslint-disable-next-line
  /* eslint-disable */
  name: 'ProductView',
  props: ['inventory', 'getClass', 'addToCart'],
  components: { ProductCard }
}
</script>