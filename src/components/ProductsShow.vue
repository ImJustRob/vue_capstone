<script>
export default {
  props: {
    product: Object,
  },
     data: function () {
     return {
       editProductParams: {},
     };
   },
   created: function () {
     this.editProductParams = { ...this.product };
   },
   methods: {
     handleSubmit: function () {
       this.$emit("updateProduct", this.product.id, this.editProductParams);
     },
   },
};
</script>

<template>
  <div>
    <h1>Product information</h1>
    <p>Name: {{ product.name }}</p>
    <p>Price: {{ product.price }}</p>
    <p>Description: {{ product.description }}</p>
    <p>Supplier Id: {{ product.supplier_id }}</p>
    <form v-on:submit.prevent="handleSubmit">
       <div>
         Name:
         <input v-model="editProductParams.name" type="text" />
       </div>
       <div>
         Price:
         <input v-model="editProductParams.price" type="text" />
       </div>
       <div>
         Description:
         <input v-model="editProductParams.description" type="text" />
       </div>
       <div>
         Supplier Id:
         <input v-model="editProductParams.supplier_id" type="text" />
       </div>
       <button type="submit">Update Product</button>
     </form>

  </div>
</template>

<style></style>