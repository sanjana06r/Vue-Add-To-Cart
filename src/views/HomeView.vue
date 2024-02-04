<template>
  <div class="home">
    <div class="splash-container">
      <div class="splash">
        <h1>Splendid Food</h1>
      </div>
    </div>

    <main class="wrapper">

      <h2>Recommended</h2>

      <div class="recommended">

        <ProductCard v-for="(product, index) in inventory" class="card" :key="product.id" :index="index" :product="product" :addToCart="addToCart" :getClass="getClass" />

      </div>

    </main>
  </div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
// @ is an alias to /src
export default {
  name: 'HomeView',
  props: ['inventory', 'getClass', 'addToCart'],
  components: { ProductCard }
}
</script>
