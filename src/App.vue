<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          AZ STORE
        </q-toolbar-title>
        <q-btn dense flat round icon="shopping_cart" />
      </q-toolbar>
    </q-header>

    <!-- Main Content -->
    <q-page-container>
      <q-page padding class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          arrows
          infinite
          animated
          control-color="black"
          swipeable
          transition-prev="slide-right"
          transition-next="slide-left"
          height="550px"
          class="bg-dark text-white shadow-2 rounded-borders"
        >
          <q-carousel-slide v-for="(image, index) in carouselImages" :key="index" :name="index" :img-src="image">
          </q-carousel-slide>
        </q-carousel>

        <!-- Cards -->
        <div class="q-mt-xl row justify-center">
          <q-card v-for="product in products" :key="product.name" class="my-card q-mb-xl q-pa-md col-xs-12 col-sm-6 col-md-4 col-lg-3">
            <q-img :src="product.image" :alt="product.name" class="my-card-img">
              <q-badge color="red" floating>{{ product.discount }}Flash Sale</q-badge>
            </q-img>
            <q-card-section>
              <div class="text-h6 text-center">{{ product.name }}</div>
              <div class="text-subtitle1 text-center">{{ product.price }}</div>
            </q-card-section>
            <q-card-actions align="center">
              <q-btn flat label="Add to Cart" color="primary" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-blue-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          &copy; Store2024 
        </q-toolbar-title>
        <div>
          <q-btn flat round icon="facebook" />
          <q-btn flat round icon="twitter" />
          <q-btn flat round icon="instagram" />
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref(0);
    const carouselImages = [
      'https://down-id.img.susercontent.com/file/id-11134201-7r990-lvjo98de2zrne8',  // Ganti dengan URL gambar Anda
      'https://down-id.img.susercontent.com/file/id-11134201-7r98x-lvefko3thc3nd0',
      'https://down-id.img.susercontent.com/file/id-11134201-7r98v-lusvzsrepuqqd2',
      'https://down-id.img.susercontent.com/file/id-11134207-7quky-li9nohxax17u67'
    ];
    const products = [
      { name: 'Tas 1', price: 'Rp. 1.200K', image: 'https://i.pinimg.com/564x/be/e7/a6/bee7a67f32ec3e23f5e85c683fe7062f.jpg'},  // Ganti dengan URL gambar Anda
      { name: 'Sepatu 2', price: 'Rp. 450K', image: 'https://down-id.img.susercontent.com/file/0e473353b14420b53df88e4fbe0de3d2'},
      { name: 'Topi 3', price: 'Rp. 145K', image: 'https://down-id.img.susercontent.com/file/3a546b179338e48768d0f9585b5f755c'},
      { name: 'Tas 4', price: 'Rp. 180K', image: 'https://down-id.img.susercontent.com/file/70b043d27c0eab1592c6d3d2e1c3496e'}
    ];

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    return {
      leftDrawerOpen,
      toggleLeftDrawer,
      slide,
      carouselImages,
      products
    };
  }
};
</script>

<style>
.my-card {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
.my-card-img {
  border-radius: 10px 10px 0 0;
  height: 250px;
}
.rounded-borders {
  border-radius: 10px;
}
.q-footer {
  border-top: 1px solid #003285;
}
</style>
