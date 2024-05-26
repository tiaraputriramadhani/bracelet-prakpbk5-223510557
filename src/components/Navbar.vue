<template>
  <div>
    <q-header elevated class="navbar-header">
      <q-toolbar>
        <q-btn flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>je bracelets</q-toolbar-title>
        <q-btn flat round label="Home" @click="navigateToHome" class="q-mr-md" />
        <q-btn flat round label="About Us" @click="navigateToAbout" />
        <q-btn flat round icon="shopping_cart" @click="toggleRightDrawer">
          
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" bordered content-class="drawer-background">
      <q-list>
        <q-item clickable v-ripple @click="selectCategory('Bracelet')">
          <q-item-label class="product-label">Product</q-item-label>
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
    },
    selectSubCategory(subCategory) {
      this.$emit('subCategorySelected', subCategory);
    }
  }
};
</script>

<style scoped>
.navbar-header {
  background-color: rgb(176, 4, 239);
  color: white;
  font-family:'Times New Roman', Times, serif;
}

.product-label {
  font-size: 1.5em; 
  font-family:'Times New Roman', Times, serif;
}

</style>
