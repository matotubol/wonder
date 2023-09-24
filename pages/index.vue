<template>
  <div class="image-container">
    <div v-for="item in images" :key="item.src" class="image-box" @click="openImage(item.src)" :style="{ width: item.width + 'px' }">
      <img :src="item.src" :alt="item.alt" class="image" />
    </div>
    <div v-if="selectedImage" class="overlay" @click="closeImage">
      <img :src="selectedImage" class="overlay-image" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        { src: '/img/1.jpg', alt: 'Image 1', width: 600 },
        { src: '/img/2.jpeg', alt: 'Image 1', width: 360 },
        { src: '/img/3.jpg', alt: 'Image 2', width: 360 },
        { src: '/img/1.jpg', alt: 'Image 1', width: 340 },

        // ... add the paths, alt texts, and widths for all your images
      ],
      selectedImage: null,
    };
  },
  
  methods: {
    openImage(src) {
      this.selectedImage = src;
    },
    closeImage() {
      this.selectedImage = null;
    },
  },
};
</script>

<style lang="scss" scoped>
.image-container {
  max-width: 970px;
  margin: auto;
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
}
.image-box {
  position: relative;
}
.image {
  display: block;
  width: 100%;
  height: auto;
}
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
}
.overlay-image {
  max-width: 90%;
  max-height: 90%;
}
</style>
