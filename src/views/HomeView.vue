<template>
  <div class="home">
    <h1 class="TopHeader">Jenill's 21st Birthday</h1>
    <!-- <h2 class="TopText">Can You Believe It?</h2> -->

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
.home {
  display: grid;
  background-color: lavenderblush;
  justify-content: center;
  align-items: center;
}

.TopHeader {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  grid-row: 1;
  
  font-family: "Brush Script MT", "Lucida Handwriting", cursive;
  font-size: 60px;
  color:palevioletred;
  text-shadow: 
    -1px -1px 0 white,
    1px -1px 0 white,
    -1px 1px 0 white,
    1px 1px 0 white;

}

.TopText {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  grid-row: 2;
  
  /* font-family: "Brush Script MT", "Lucida Handwriting", cursive;
  font-size: 60px;
  color:palevioletred;
  text-shadow: 
    -1px -1px 0 white,
    1px -1px 0 white,
    -1px 1px 0 white,
    1px 1px 0 white; */
}

.slider {
  overflow: hidden;
  width: 415.5px; /* 277px width */
  height: 525px; /* 350px height */
  position: relative;
  
  display: flex; 
  justify-content: center; 
  align-items: center;
  grid-row: 3;
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

@media (max-width: 450px) {
  .slider {
    width: 80%;
    max-width: none;
    height: auto;
    margin: 0 auto;
  }
}

</style>
