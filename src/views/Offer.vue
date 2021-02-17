<template>
  <div class="offer">
    <h1>Oferta</h1>
    <Product
      v-for="(item, index) of products"
      :key="index"
      :item="item"
    />
  </div>
</template>

<script>
  import Product from "../components/Product.vue"

  export default {
    components: {
      Product
    },
    data () {
      return {
        products: []
      }
    },
    mounted() {
      let req = new XMLHttpRequest();

      req.open('GET', '/text.json', false);
      req.send(null);

      if (req.status == 200) {
        this.products = JSON.parse(req.responseText).products
      }
    }
  }
</script>

<style scoped lang="scss">
  .offer {
    min-height: 1200px;
    padding: 150px 20px 200px 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>