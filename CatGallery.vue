<!-- CatGallery.vue -->
<template>
  <div class="cat-gallery">
    <div class="grid">
      <CatImage v-for="(image, index) in images" :key="index" :imageUrl="image.url" />
    </div>
    <button @click="loadMoreImages">Load More Images</button>
  </div>
</template>

<script>
import CatImage from './CatImage.vue';

export default {
  name: 'CatGallery',
  components: {
    CatImage
  },
  data() {
    return {
      images: []
    };
  },
  created() {
    this.loadMoreImages();
  },
  methods: {
    async loadMoreImages() {
      try {
        const response = await fetch('https://cataas.com/api/cats?limit=10');
        const data = await response.json();
        console.log('Fetched data:', data); // Log fetched data for debugging
        const images = data.map(cat => ({ url: `https://cataas.com/cat/${cat.id}` }));
        this.images = [...this.images, ...images];
      } catch (error) {
        console.error('Error fetching cat images:', error);
      }
    }
  }
}
</script>


<style scoped>
/* Scoped styles for CatGallery.vue */
</style>