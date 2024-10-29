<script>
  import axios from "axios";
  import ProductsIndex from "./ProductsIndex.vue";

  export default {
    components: {
      ProductsIndex,
    },
    data: function () {
      return {
        products: [],
      };
    },
   created: function () {
     this.handleIndexProducts();
   },
   methods: {
     handleIndexProducts: function () {
       axios.get("http://localhost:3000/products.json").then((response) => {
         console.log("products index", response);
         this.products = response.data;
       });
     },
   },
  };
  </script>

  <template>
    <main>
      <ProductsIndex v-bind:products="products" />
    </main>
  </template>

  <style></style>