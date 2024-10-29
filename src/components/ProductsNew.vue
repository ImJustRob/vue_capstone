<script>
 export default {
   data: function () {
     return {
       newProductParams: {},
     };
   },
   methods: {
     handleSubmit: function () {
       this.$emit("createProduct", this.newProductParams);
       this.newProductParams = {};
     },
   },
 };
</script>

<template>
  <div>
    <h1>New Product</h1>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Name:
        <input type="text" v-model="newProductParams.name" />
      </div>
      <div>
        Price:
        <input type="text" v-model="newProductParams.price" />
      </div>
      <div>
        Description:
        <input type="text" v-model="newProductParams.description" />
      </div>
      <div>
        Supplier Id:
        <input type="text" v-model="newProductParams.supplier_id" />
      </div>
      <button type="submit">Create Product</button>
    </form>
  </div>
</template>

<style></style>