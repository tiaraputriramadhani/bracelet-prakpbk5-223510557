<template>
  <q-layout view="hHh lpR fFf">
    <Navbar @categorySelected="selectCategory" @subCategorySelected="selectSubCategory" @aboutUsSelected="showAboutUs" :cartItems="cartItems" />

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
            <q-carousel-slide :name="1" img-src="./assets/foto3.jpg" />
            <q-carousel-slide :name="2" img-src="./assets/foto1.jpg" />
            <q-carousel-slide :name="3" img-src="./assets/carou1.jpg" />
            <q-carousel-slide :name="4" img-src="./assets/cewe2.jpg" />
          </q-carousel>
        </div>
      </div>

      <q-page padding>
        <div v-if="selectedCategory === 'Bracelet'" class="text-center Bracelet-background">
          <h2>BRACELET</h2>
          <q-btn-group outline>
            <q-btn label="Pria" @click="selectSubCategory('Pria')" />
            <q-btn label="Wanita" @click="selectSubCategory('Wanita')" />
          </q-btn-group>
          <br>
          <br>
          
          <div class="q-gutter-md row justify-around">
            <ProductCard
              v-for="product in (selectedSubCategory === 'Pria' ? BraceletPria : selectedSubCategory === 'Wanita' ? BraceletWanita : [])"
              :key="product.id"
              :product="product"
              @addToCart="addToCart"
            />
          </div>
         
        </div>
        <div v-if="selectedCategory === 'About'">
          <About />
        </div>
        <div v-else-if="selectedCategory === null">
          <img src="./assets/carou1.jpg">
          <img src="./assets/carou1.jpg" alt="Nama Produk" class="full-screen-image">
        </div>
      </q-page>
    </q-page-container>

    <Footer/>
  </q-layout>
</template>

<script>
import { ref } from 'vue';
import Navbar from './components/Navbar.vue';
import ProductCard from './components/kotakproduk.vue';
import Footer from './components/Footer.vue';
import About from './components/About.vue';

import Bracel1 from './assets/cowo1.jpg';
import Bracel2 from './assets/cowo2.jpg';
import Bracel3 from './assets/cowo3.jfif';
import Bracel4 from './assets/cowo4.jpg';
import Bracel5 from './assets/product1.jpg';
import Bracel6 from './assets/cewe2.jpg';
import Bracel7 from './assets/cewe4.jfif';
import Bracel8 from './assets/cewe3.jpg';

export default {
  name: 'App',
  components: {
    Navbar,
    ProductCard,
    Footer,
    About
  },
  setup() {
    const selectedCategory = ref('Home');
    const selectedSubCategory = ref(null);
    const cartItems = ref([]);
    const carouselIndex = ref(0);
    const slide = ref(1);

    const BraceletPria = ref([
      { id: 1, name: 'Man Quality Leather', price: 'RP. 120.000', image: Bracel1 },
      { id: 2, name: 'Man Black Leather', price: 'RP. 50.000', image: Bracel2 },
      { id: 2, name: 'Brown Barcelet Man', price: 'RP. 100.000', image: Bracel3 },
      { id: 2, name: 'Gradient Silver barcelet ', price: 'RP. 20.000', image: Bracel4 },
      
    ]);

    const BraceletWanita = ref([
      { id: 3, name: 'Madison Bracelet', price: 'RP. 15.000', image: Bracel5 },
      { id: 4, name: 'whiter Mode Debora', price: 'RP.25.000', image: Bracel6 },
      { id: 5, name: 'Pandora Rose Gold', price: 'RP.225.000', image: Bracel7 },
      { id: 6, name: 'Pandora Bracelet Gold', price: 'RP.425.000', image: Bracel8 },
     
    ]);

    const selectCategory = (category) => {
      selectedCategory.value = category;
      selectedSubCategory.value = null;
    };

    const selectSubCategory = (subCategory) => {
      selectedSubCategory.value = subCategory;
    };

    const showAboutUs = () => {
      selectedCategory.value = 'About';
    };

    const addToCart = (product) => {
      cartItems.value.push(product);
    };

    return {
      selectedCategory,
      selectedSubCategory,
      BraceletPria,
      BraceletWanita,
      cartItems,
      carouselIndex,
      slide,
      selectCategory,
      selectSubCategory,
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


.small-image {
  width: 45%; 
  max-height: 400px; 
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
  height: 600px;
}

.full-screen-image {
  width: 100%;
  height: 100vh;
  object-fit: cover;
  margin-bottom: 20px;
}

.Bracelet-background {
  background-color: #f5f5f5;
  padding: 20px;
}

</style>
