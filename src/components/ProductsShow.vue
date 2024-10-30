<script>
export default {
  props: {
    product: Object,
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
  </div>
</template>

<style></style>