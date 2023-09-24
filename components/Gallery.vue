<template>
  <button @click="addItem">Add</button>
  <div class="grid" ref="masonry">
    <div class="grid-item"></div>
    <div v-for="item in items" class="grid-item" :class="item.classes"></div>
  </div>
</template>

<script>

const ITEM_CLASSES = ['grid-item--width2 grid-item--height2', 'grid-item--width2', 'grid-item--height2']

const randomInt = (min = 1, max = ITEM_CLASSES.length) => Math.floor(Math.random() * (max - min) + min)

const randItemClass = () => ITEM_CLASSES[randomInt()]

export default {
  data() {
    return {
      items: [],
    }
  },
  mounted() {
    this.$nextTick(() => this.layout())
  },
  updated() {
    this.layout()
  },
  methods: {
    addItem() {
      this.items.push({ classes: randItemClass() })
    },
    layout() {
      this._masonry = new Masonry(this.$refs.masonry, {
        itemSelector: '.grid-item',
        columnWidth: 160,
        percentPosition: true,
      })
    },
  },
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.grid {
  background: #eee;
  max-width: 1200px;
}
.grid-item {
  width: 160px;
  height: 120px;
  float: left;
  background: #d26;
  border: 2px solid #333;
  border-color: hsla(0, 0%, 0%, 0.5);
  border-radius: 5px;
}
.grid-item--width2 {
  width: 320px;
}
.grid-item--width3 {
  width: 480px;
}
.grid-item--width4 {
  width: 640px;
}

.grid-item--height2 {
  height: 200px;
}
.grid-item--height3 {
  height: 260px;
}
.grid-item--height4 {
  height: 360px;
}
</style>
