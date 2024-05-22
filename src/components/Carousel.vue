<!-- src/components/Carousel.vue -->
<template>
    <q-carousel
      v-model="slide"
      animated
      swipeable
      infinite
      arrows
      navigation
    >
      <q-carousel-slide
        v-for="img in images"
        :key="img"
        :name="img"
        :img-src="img"
      />
    </q-carousel>
  </template>
  
  <script>
  export default {
    name: 'Carousel',
    data() {
      return {
        slide: 0,
        images: [
          'https://via.placeholder.com/800x400?text=Slide+1',
          'https://via.placeholder.com/800x400?text=Slide+2',
          'https://via.placeholder.com/800x400?text=Slide+3'
        ]
      }
    }
  }
  </script>
  <style scoped>
.carousel-container {
  background-color: #f8f8f8; /* Ubah warna latar belakang carousel container */
}

.carousel-slide {
  border-radius: 10px; /* Beri radius sudut pada carousel slide */
}

.carousel-slide img {
  border-radius: 10px; /* Beri radius sudut pada gambar dalam carousel */
}
</style>