<template>
  <div class="product">
    <h3>{{ product.name }}</h3>
    <p>{{ product.description }}</p>
    <Add v-bind:product="product"/>
  </div>
</template>

<script>
import Add from './Add'
export default {
  name: "Product",
  props: {
    product: Object
  },
  components: {
    Add
  }
}
</script>

<style scoped lang="scss">
.product {
  margin: 0 60px;
  border-top: 3px solid #e62f35;
}
</style>
