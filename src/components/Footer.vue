<template>
  <q-footer class="footer">
    <q-toolbar>
      <q-toolbar-title class="footer-title">
        &copy; 2024 Thrif Shop
      </q-toolbar-title>
      <div class="footer-icons">
        Follow us:
        <q-icon name="facebook" class="footer-icon" />
        <q-icon name="twitter" class="footer-icon" />
        <q-icon name="instagram" class="footer-icon" />
      </div>
    </q-toolbar>
  </q-footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background-color: black; /* Mengubah warna latar belakang menjadi hitam */
  color: white; /* Mengubah warna teks menjadi putih */
}

.footer-title {
  color: white; /* Mengubah warna teks judul footer menjadi putih */
}

.footer-icons {
  color: white; /* Mengubah warna teks di sekitar ikon menjadi putih */
}

.footer-icon {
  color: white; /* Mengubah warna ikon footer menjadi putih */
  margin-left: 10px; /* Menambahkan margin kiri untuk memberikan ruang antara ikon */
}
</style>
