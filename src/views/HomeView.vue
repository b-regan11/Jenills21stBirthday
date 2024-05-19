<template>
  <div class="home">
    <h1>Jenill's 21st Birthday</h1>
    <div class="slider">
      <div class="slider-wrapper" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div v-for="(image, index) in images" :key="index" class="slide">
          <img :src="image" :alt="'Slide ' + index" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      images: [
        require('@/assets/Jenill1.jpeg'),
        require('@/assets/Jenill2.jpeg'),
        require('@/assets/Jenill3.jpeg'),
        require('@/assets/Jenill4.jpeg'),
        require('@/assets/Jenill5.jpeg'),
        require('@/assets/Jenill6.jpeg'),
        require('@/assets/Jenill7.png'),
      ]
    };
  },
  mounted() {
    this.startSlider();
    this.setRandomStart();
    this.setTitle();
  },
  methods: {
    startSlider() {
      setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.images.length;
      }, 10000); // Change slide every 10 seconds
    },
    setRandomStart() {
      this.currentIndex = Math.floor(Math.random() * this.images.length);
    },
    setTitle() {
      document.title = "Jenill's Birthday";
    }
  }
};
</script>

<style scoped>
.slider {
  overflow: hidden;
  width: 277px;
  height: 350px;
  position: relative;
}

.slider-wrapper {
  display: flex;
  transition: transform 0.5s ease;
}

.slide {
  min-width: 100%;
  height: 100%;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.home {
  background-color: lavenderblush;
}

</style>
