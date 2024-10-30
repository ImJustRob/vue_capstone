<script>
  import axios from "axios";
  import ProductsIndex from "./ProductsIndex.vue";
  import ProductsNew from "./ProductsNew.vue";
  import ProductsShow from "./ProductsShow.vue";
  import Modal from "./Modal.vue";

  export default {
    components: {
      ProductsIndex,
      ProductsNew,
      ProductsShow,
      Modal,
    },
    data: function () {
      return {
        products: [],
        currentProduct: {},
       isProductsShowVisible: false,
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
          handleCreateProduct: function (params) {
       axios
         .post("http://localhost:3000/products.json", params)
         .then((response) => {
           console.log("products create", response);
           this.products.push(response.data);
         })
         .catch((error) => {
           console.log("products create error", error.response);
         });
     },
     handleShowProduct: function (product) {
       console.log("handleShowProduct", product);
       this.currentProduct = product;
       this.isProductsShowVisible = true;
     },

     handleUpdateProduct: function (id, params) {
       console.log("handleUpdateProduct", id, params);
       axios
         .patch(`http://localhost:3000/products/${id}.json`, params)
         .then((response) => {
           console.log("products update", response);
           this.products = this.products.map((product) => {
             if (product.id === response.data.id) {
               return response.data;
             } else {
               return product;
             }
           });
           this.handleClose();
         })
         .catch((error) => {
           console.log("products update error", error.response);
         });
     },
     handleDestroyProduct: function (product) {
       axios.delete(`http://localhost:3000/products/${product.id}.json`).then((response) => {
         console.log("products destroy", response);
         var index = this.products.indexOf(product);
         this.products.splice(index, 1);
         this.handleClose();
       });
     },

     handleClose: function () {
       this.isProductsShowVisible = false;
     },
   },
  };
  </script>

  <template>
    <main>
      <ProductsNew v-on:createProduct="handleCreateProduct" />
      <ProductsIndex v-bind:products="products" v-on:showProduct="handleShowProduct" />
      <Modal v-bind:show="isProductsShowVisible" v-on:close="handleClose">
        <ProductsShow v-bind:product="currentProduct" v-on:updateProduct="handleUpdateProduct" v-on:destroyProduct="handleDestroyProduct" />
     </Modal>
    </main>
  </template>

  <style></style>