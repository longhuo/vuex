<template>
    <div>
      <h1>Shopping Cart</h1>
      <ul>
        <li v-for="product in products" v-bind:key="product.id">
          {{product.title}} - {{product.price | currency}} - {{product.quantity}}
        </li>
      </ul>
      <p>Total: {{total | currency}}</p>
      <button @click="checkout">Checkout</button>
      <p v-if="checkoutStatus">{{checkoutStatus}}</p>
      <button @click="clear">Clear</button>
    </div>
</template>

<script>
  import {mapState, mapGetters, mapActions} from 'vuex'
  export default {
    computed: {
      ...mapGetters('cart', {
        products: 'cartProducts',
        total: 'cartTotal'
      }),

      ...mapState('cart', {
        checkoutStatus: state => state.checkoutStatus
      })
    },

    methods: {
      ...mapActions('cart', ['checkout', 'clear'])
    }
  }
</script>

<style scoped>

</style>
