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
  background-color: #fff; /* Ubah warna latar belakang kartu produk */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Beri bayangan kartu produk */
}

.product-image {
  width: 100%;
  height: 250px; /* Set the desired height */
  object-fit: cover; /* Ensures the image covers the box without distortion */
  border-top-left-radius: 10px; /* Beri radius sudut pada gambar atas kiri */
  border-top-right-radius: 10px; /* Beri radius sudut pada gambar atas kanan */
}
</style>
