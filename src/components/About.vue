<!-- src/components/About.vue -->
<template>
    <div class="about-page">
      <h1>About Us</h1>
      <p>
        Selamat datang di toko online kami! Kami berdedikasi untuk menyediakan Anda dengan produk kualitas terbaik dengan harga terbaik. kami sangat tertarik dengan fashion dan kami berusaha untuk memberikan Anda tren terbaru dan klasik abadi.
      </p>
      <p>
        Terima kasih telah memilih kami untuk kebutuhan belanja Anda. Kami harap Anda menikmati pengalaman Anda bersama kami!
      </p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'About'
  };
  </script>
  
  <style scoped>
  .about-page {
    background-color: #f5f5f5;
    padding: 20px;
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }
  
  .about-page h1 {
    margin-bottom: 20px;
  }
  
  .about-page p {
    font-size: 1.1em;
    line-height: 1.6;
    margin-bottom: 20px;
  }
  </style>
  