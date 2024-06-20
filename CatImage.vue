<!-- src/components/CatImage.vue -->
<template>
  <div class="cat-image">
    <img :src="imageUrl" alt="Cat Image" />
  </div>
</template>

<script>
export default {
  name: 'CatImage',
  props: {
    imageUrl: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.cat-image {
  margin: 10px;
}
.cat-image img {
  width: 100%;
  height: auto;
  border-radius: 8px;
}
</style>