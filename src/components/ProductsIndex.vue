<script>
 export default {
   props: {
     products: Array,
   },
 };
  </script>

  <template>
    <div>
      <h1>All products</h1>
     <div v-for="product in products" v-bind:key="product.id">
       <h2>{{ product.name }}</h2>
       <img v-bind:src="product.url" />
       <p>Price: {{ product.price }}</p>
       <p>Description: {{ product.description }}</p>
       <p>Supplier Id: {{  product.supplier_id }}</p>
       <button v-on:click="$emit('showProduct', product)">More info</button>
     </div>
    </div>
  </template>

  <style></style>