<template>
    <q-card class="product-card">
      <q-img :src="product.image" class="product-image" />
      <q-card-section>
        <div class="text-h6">{{ product.name }}</div>
        <div class="text-subtitle2">{{ product.price }}</div>
      </q-card-section>
      <q-card-actions align="right">
        <q-btn flat label="Tambahkan Ke keranjang" @click="addToCart" />
      </q-card-actions>
    </q-card>
  </template>
  
  <script>
  export default {
    name: 'ProductCard',
    props: {
      product: {
        type: Object,
        required: true
      }
    },
    methods: {
      addToCart() {
        this.$emit('addToCart', this.product);
      }
    }
  };
  </script>
  
  <style scoped>
  .product-card {
    width: 250px;
    margin: 10px;
    background-color: #fff;
    
  }
  
  .product-image {
    width: 100%;
    height: 250px; 
    object-fit: cover; 
    border-top-left-radius: 10px; 
    border-top-right-radius: 10px; 
  }
  </style>
  