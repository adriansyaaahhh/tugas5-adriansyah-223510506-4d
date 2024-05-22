<!-- src/App.vue -->
<template>
  <q-layout view="hHh lpR fFf">
    <Navbar @categorySelected="selectCategory" @aboutUsSelected="showAboutUs" :cartItems="cartItems" />

    <q-page-container>
      <div v-if="selectedCategory === 'Home'" class="home">
        <h2 class="section-title"></h2>
        <div class="carousel-container">
          <q-carousel
            animated
            v-model="slide"
            arrows
            navigation
            infinite
            class="carousel"
          >
            <q-carousel-slide :name="1" img-src="./assets/rp.jpg" />
            <q-carousel-slide :name="2" img-src="./assets/iklan1.jpg" />
            <q-carousel-slide :name="3" img-src="./assets/perry.jpg" />
            <q-carousel-slide :name="4" img-src="./assets/leviss.jpg" />
          </q-carousel>
        </div>
      </div>

      <q-page padding>
        <div v-if="selectedCategory === 'Baju Kaos'" class="text-center baju-kaos-background">
          <h2>T-Shirt</h2>
          <div class="q-gutter-md row justify-around">
            <ProductCard v-for="product in bajuKaosProducts" :key="product.id" :product="product" @addToCart="addToCart" />
          </div>
        </div>
        <div v-if="selectedCategory === 'Kemeja'" class="text-center kemeja-background">
          <h2>Kemeja</h2>
          <div class="q-gutter-md row justify-around">
            <ProductCard v-for="product in kemejaProducts" :key="product.id" :product="product" @addToCart="addToCart" />
          </div>
        </div>
        <div v-if="selectedCategory === 'Celana'" class="text-center celana-background">
          <h2>Celana</h2>
          <div class="q-gutter-md row justify-around">
            <ProductCard v-for="product in celanaProducts" :key="product.id" :product="product" @addToCart="addToCart" />
          </div>
        </div>
        <div v-if="selectedCategory === 'About'">
          <About />
        </div>
        <div v-else-if="selectedCategory === null">
          <img src="./assets/iklankaos.jpg">
          <img src="./assets/kaos3.jpg" alt="Nama Produk" class="full-screen-image">
        </div>
      </q-page>
    </q-page-container>

    <Footer />
  </q-layout>
</template>

<script>
import { ref } from 'vue';
import Navbar from './components/Navbar.vue';
import ProductCard from './components/ProductCard.vue';
import Footer from './components/Footer.vue';
import About from './components/About.vue';

import kaos1 from './assets/kaos1.jpg';
import kaos2 from './assets/kaos2.jfif';
import kaos3 from './assets/kaos3.jpg';
import kaos4 from './assets/kaos4.jpg';

import kemeja1 from './assets/kemeja1.jfif';
import kemeja2 from './assets/kemeja2.jfif';
import kemeja3 from './assets/kemeja3.jpg';
import kemeja4 from './assets/kemeja4.jfif';

import celana1 from './assets/celana1.jpg';
import celana2 from './assets/celana2.jpg';
import celana3 from './assets/celana3.jfif';
import celana4 from './assets/celana4.jpg';

export default {
  name: 'App',
  components: {
    Navbar,
    ProductCard,
    Footer,
    About
  },
  setup() {
    const selectedCategory = ref('Home'); // Default category is 'Home'
    const cartItems = ref([]);
    const carouselIndex = ref(0);
    const slide = ref(1);

    const bajuKaosProducts = ref([
      { id: 1, name: 'Rucas Year Of Dragon Tee ', price: 'RP. 850.000', image: kaos1 },
      { id: 2, name: 'The Initial Hand Stitch Black ', price: 'RP. 450.000', image: kaos2 },
      { id: 3, name: 'T-Shirt Polo Ralph Lauren USA    ', price: 'RP.550.000', image: kaos3 },
      { id: 4, name: 'Polo By Ralph Lauren', price: 'RP.355.000', image: kaos4 }
    ]);

    const kemejaProducts = ref([
      { id: 1, name: 'Slevee Lacose Ralph lauren', price: 'RP.350.000', image: kemeja1 },
      { id: 2, name: 'Kemeja long Flannel By Uniqlo', price: 'RP.200.000', image: kemeja2 },
      { id: 3, name: 'Kemeja Long sleeve By Uniqlo', price: 'RP.300.000', image: kemeja3 },
      { id: 4, name: 'Kemeja Burberry Mirror Classic', price: 'RP.350.000', image: kemeja4 }
    ]);

    const celanaProducts = ref([
      { id: 1, name: 'Jeans Levis 505 Slim Straight', price: 'RP400.000', image: celana1 },
      { id: 2, name: 'Wrangler Denim GrensBoro ', price: 'RP. 349.000', image: celana2 },
      { id: 3, name: 'Rucas Season 9 Grand Black Jeans ', price: 'RP.650.000', image: celana3 },
      { id: 4, name: 'Rucas Cavier Leather Navy Jeans', price: 'RP.550.000', image: celana4 }
    ]);

    const selectCategory = (category) => {
      selectedCategory.value = category;
    };

    const showAboutUs = () => {
      selectedCategory.value = 'About';
    };

    const addToCart = (product) => {
      cartItems.value.push(product);
    };

    return {
      selectedCategory,
      bajuKaosProducts,
      kemejaProducts,
      celanaProducts,
      cartItems,
      carouselIndex,
      slide,
      selectCategory,
      showAboutUs,
      addToCart
    };
  }
};
</script>

<style scoped>
.home {
  padding: 20px;
}

.section-title {
  text-align: center;
  margin-bottom: 20px;
}

.carousel-container {
  max-width: 1300px;
  margin: 0 auto;
}

.carousel {
  height: 700px;
}

.photo-box {
  border: 1px solid #ccc;
  border-radius: 8px;
}

.photo {
  width: 100%;
  height: auto;
  display: block;
}

.photo-label {
  background-color: #f0f0f0;
  padding: 10px;
  text-align: center;
}

.full-screen-image {
  width: 100%;
  height: 100vh;
  object-fit: cover;
  margin-bottom: 20px;
}

.baju-kaos-background {
  background-image: url('./assets/baju-kaos-background.jpg');
  background-size: cover;
  background-position: center;
  padding: 20px;
}

.kemeja-background {
  background-image: url('./assets/kemeja-background.jpg');
  background-size: cover;
  background-position: center;
  padding: 20px;
}

.celana-background {
  background-image: url('./assets/celana-background.jpg');
  background-size: cover;
  background-position: center;
  padding: 20px;
}
</style>
