<template>
  <div class="container">
    <masonry-wall :items="items" :ssr-columns="1" :column-width="300" :gap="7" :min-columns="1">
      <template #default="{ item, index }">
        <div class="image-box" @click="openImage(item.imageSrc, index)">
          <img :src="item.imageSrc" :alt="item.title" style="width: 100%; max-width: 980px;">
        </div>
      </template>
    </masonry-wall>
    <!-- Overlay for Fullscreen -->
    <div v-if="selectedImage" class="overlay" @click="closeImage">
      <button class="download-btn" @click.stop="downloadImage">Download</button>
      <button class="prev-btn" @click.stop="navigate(-1)">←</button>
      <img :src="selectedImage" class="overlay-image" />
      <button class="next-btn" @click.stop="navigate(1)">→</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, Ref } from 'vue';

interface Item {
  title: string;
  description: string;
  imageSrc: string;
}

const items: Item[] = [  {
    title: 'First Image',
    description: 'The first image description.',
    imageSrc: '/img/1.jpg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/2.jpeg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/3.jpg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/4.jpeg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/5.jpeg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/7.jpeg'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },
  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },  {
    title: 'Second Image',
    description: 'The second image description.',
    imageSrc: '/img/6.webp'
  },
  
  // Add more items...
];

const selectedImage: Ref<string | null> = ref(null);
const selectedIndex: Ref<number | null> = ref(null);

const openImage = (src: string, index: number): void => {
  selectedImage.value = src;
  selectedIndex.value = index;
};

const closeImage = (): void => {
  selectedImage.value = null;
  selectedIndex.value = null;
};

const navigate = (direction: number): void => {
  if (selectedIndex.value !== null) {
    const newIndex = selectedIndex.value + direction;
    if (newIndex >= 0 && newIndex < items.length) {
      selectedIndex.value = newIndex;
      selectedImage.value = items[newIndex].imageSrc;
    }
  }
};

const downloadImage = (): void => {
  if (selectedImage.value) {
    window.open(selectedImage.value, '_blank');
  }
};
</script>

<style scoped>
/* Existing Styles */
.container {
  max-width: 980px;
  margin: auto;
}
.image-box {
  position: relative;
}
/* New Styles for Overlay and Buttons */
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
.download-btn,
.prev-btn,
.next-btn {
  position: fixed;
  background: white;
  border: none;
  cursor: pointer;
  padding: 10px;
  z-index: 1;
}
.download-btn {
  top: 15px;
  right: 15px;
}
.prev-btn {
  left: 15px;
}
.next-btn {
  right: 15px;
}
</style>
