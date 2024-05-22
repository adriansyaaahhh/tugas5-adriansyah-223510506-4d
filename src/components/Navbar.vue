<!-- src/components/Navbar.vue -->
<template>
  <div>
    <q-header elevated class="navbar-header">
      <q-toolbar>
        <q-btn flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>Thrift Shop</q-toolbar-title>
        <q-btn flat round label="Home" @click="navigateToHome" class="q-mr-md" />
        <q-btn flat round label="About Us" @click="navigateToAbout" />
        <!-- Tambahkan tanda merah di sekitar ikon keranjang -->
        <q-btn flat round icon="shopping_cart" @click="toggleRightDrawer">
          <q-badge color="red" :content="cartItems.length" v-show="showCartBadge"></q-badge>
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" bordered content-class="drawer-background">
      <q-list>
        <q-item clickable v-ripple @click="selectCategory('Baju Kaos')">
          <q-item-label>Baju Kaos</q-item-label>
        </q-item>
        <q-item clickable v-ripple @click="selectCategory('Kemeja')">
          <q-item-label>Kemeja</q-item-label>
        </q-item>
        <q-item clickable v-ripple @click="selectCategory('Celana')">
          <q-item-label>Celana</q-item-label>
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer v-model="rightDrawerOpen" side="right" bordered content-class="drawer-background">
      <q-list>
        <q-item v-for="item in cartItems" :key="item.id">
          <q-item-section>{{ item.name }}</q-item-section>
          <q-item-section>{{ item.price }}</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  props: {
    cartItems: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      leftDrawerOpen: false,
      rightDrawerOpen: false
    };
  },
  computed: {
    showCartBadge() {
      return this.cartItems.length > 0;
    }
  },
  methods: {
    toggleLeftDrawer() {
      this.leftDrawerOpen = !this.leftDrawerOpen;
    },
    toggleRightDrawer() {
      this.rightDrawerOpen = !this.rightDrawerOpen;
    },
    navigateToHome() {
      this.$emit('categorySelected', 'Home');
    },
    navigateToAbout() {
      this.$emit('aboutUsSelected');
    },
    selectCategory(category) {
      this.toggleLeftDrawer();
      this.$emit('categorySelected', category);
    }
  }
};
</script>

<style scoped>
.navbar-header {
  background-color: black; /* Mengubah warna latar belakang menjadi hitam */
}

.q-toolbar-title {
  color: white; /* Mengubah warna teks menjadi putih untuk kontras yang lebih baik */
}

.q-btn {
  color: white; /* Mengubah warna teks tombol menjadi putih untuk kontras yang lebih baik */
}

.q-badge {
  background-color: red; /* Warna badge */
}
</style>