<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <div @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>
  <router-view :inventory="inventory" :addToCart="addToCart" :getClass="getClass" />
  <SideBar v-if="showSidebar" :cart="cart" :toggle="toggleSidebar" :inventory="inventory" :remove="removeItem" />
</template>

<script>
// eslint-disable-next-line
/* eslint-disable */
import SideBar from '@/components/SideBar'
import food from './food.json'
export default {
  data () {
    return {
      showSidebar: false,
      inventory: food,
      cart: {}
    }
  },
  components: {
    SideBar
  },
  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    },
    getClass () {
      return ind => {
        return 'icofont-10x icofont-' + this.inventory[ind].icon
      }
    }
  },
  methods: {
    addToCart (name, index, quantity) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += quantity
      quantity = 1
      console.log(this.cart)
    },
    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },
    removeItem (name) {
      delete this.cart[name]
    }
  }
}

</script>
